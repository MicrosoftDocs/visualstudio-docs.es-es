---
title: Cambios importantes en la API en Visual Studio versión preliminar de 2022
description: Obtenga información sobre los cambios de API que hacen que las extensiones de VS existentes no se compilen al migrar extensiones a Visual Studio versión preliminar de 2022.
ms.date: 06/08/2021
ms.topic: reference
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 9427b7a75ad53fc9a0795b249d96431113aba36d
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308624"
---
# <a name="breaking-api-changes-in-visual-studio-2022"></a>Cambios importantes en la API en Visual Studio 2022

[!INCLUDE [preview-note](../includes/preview-note.md)]

Si va a migrar una extensión a Visual Studio 2022, los cambios importantes que se enumeran aquí podrían afectarle.

## <a name="reference-assemblies-no-longer-installed"></a>Los ensamblados de referencia ya no están instalados

Muchos de los ensamblados a los que puede haber hecho referencia es a que MSBuild se resolvió desde un Visual Studio de instalación ya no están instalados. Debe usar NuGet para adquirir los ensamblados Visual Studio referencia del SDK que necesita. Consulte [Modernización de proyectos](update-visual-studio-extension.md#modernize-your-vsix-project) para obtener pasos detallados sobre cómo hacerlo.

## <a name="removed-apis"></a>API eliminadas

En Visual Studio 2022 se han quitado varias API como parte de la Visual Studio a partir de ahora. Puede encontrar una lista de las API quitadas en la [página Lista de API eliminadas.](removed-api-list.md)

## <a name="interop-breaking-changes"></a>Cambios importantes en la interoperabilidad

Muchas de nuestras API han cambiado en Visual Studio 2022, normalmente con cambios simples que son sencillos para que el código se alome.

Para administrar los cambios importantes, tenemos previsto proporcionar un nuevo mecanismo para la distribución de ensamblados de interoperabilidad. En concreto, para Visual Studio 2022 y posteriores, proporcionamos un único ensamblado de interoperabilidad con definiciones para muchas interfaces Visual Studio públicos comunes. Ese ensamblado contiene definiciones administradas para muchas interfaces Visual Studio que se alejan de varios ensamblados de interoperabilidad. El nuevo ensamblado de interoperabilidad se distribuye a través del `Microsoft.VisualStudio.Interop` paquete NuGet.

Sin embargo, Visual Studio componentes que se usan principalmente en contextos nativos y tienen un número bajo de cambios importantes seguirán teniendo sus propios ensamblados de interoperabilidad (por ejemplo, el ensamblado del depurador seguirá VisualStudio.Debugger.Interop.dll como lo hace actualmente). En cualquier caso, se puede hacer referencia a los ensamblados desde la aplicación, tal y como están en la actualidad.

Se trata de un cambio significativo y significa que las extensiones que usan api en y ensamblados integrados en este nuevo enfoque no son compatibles con las versiones anteriores de Visual Studio mediante el ensamblado de interoperabilidad anterior.

Esto tiene algunas ventajas muy importantes que facilitarán la actualización de la extensión a Visual Studio 2022:

- Las API rotas se convertirán en errores de tiempo de compilación, lo que facilita su búsqueda y corrección.
- Solo necesita actualizar el código que usa una API que se ha roto en Visual Studio 2022.
- No podrá usar accidentalmente la API antigua, ahora rota.

En general, estos cambios darán lugar a una versión más estable de Visual Studio para todos los usuarios. La principal desventaja de este enfoque es que los ensamblados administrados no podrán ejecutarse en Visual Studio 2019 y Visual Studio 2022 sin compilar el código una vez para cada versión de destino Visual Studio.

A medida que se trabaja con errores de compilación debido a las diferencias de API entre Visual Studio 2019 y Visual Studio 2022, puede encontrar la API o el patrón al que se enfrenta a continuación con instrucciones sobre cómo corregirlo.

### <a name="int-or-uint-where-intptr-is-expected"></a>`int` o `uint` donde `IntPtr` se espera

Esperamos que este sea un error muy común. Para que Visual Studio 2022 sea un proceso de 64 bits, algunas de nuestras API de interoperabilidad tenían que ser fijas donde se supone que un puntero podría caber en un entero de 32 bits para usar realmente un valor de tamaño de puntero.

Error de ejemplo:

> Argumento 3: no se puede convertir de 'out uint' a 'out System.IntPtr'

Simplemente actualice el código para esperar o proporcionar `IntPtr` o dónde o solía ser para resolver la `UIntPtr` `int` `uint` interrupción.

Corrección de ejemplo:

```diff
-shell.LoadLibrary(myGuid, myFlags, out uint ptrLib);
+shell.LoadLibrary(myGuid, myFlags, out IntPtr ptrLib);
```

### <a name="an-interop-type-defined-in-two-assemblies"></a>Tipo de interoperabilidad definido en dos ensamblados

Cuando el compilador de C# notifica un error que indica que un tipo que está usando está definido en dos ensamblados, probablemente haga referencia a un ensamblado de la versión Visual Studio 2019 del SDK a la que ya no debe hacer referencia.

Error de ejemplo:

> error CS0433: El tipo "IVsDpiAware" existe en "Microsoft.VisualStudio.Interop, Version=17.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" y "Microsoft.VisualStudio.Shell.Interop.16.0.DesignTime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

Consulte nuestra tabla [de reapping](migrated-assemblies.md) de ensamblados de referencia para ver qué nombre de ensamblado es el nombre preferido en Visual Studio 2022.
Teniendo en cuenta los dos ensamblados denominados en el error de ejemplo anterior y observando esta tabla, observe que `Microsoft.VisualStudio.Interop` es el nuevo nombre de ensamblado. A continuación, la corrección sería quitar la referencia `Microsoft.VisualStudio.Shell.Interop.16.0.DesignTime` a del proyecto.

En algunos casos, ofrecemos un paquete Visual Studio versión 2022 para el ensamblado en desuso que contiene reenviadores de tipos. Cuando esté disponible, tiene la  opción de actualizar la referencia del paquete a la versión Visual Studio 2022 en lugar de quitarla. Los reenviadores de tipos resolverán el error del compilador.

Tenga en cuenta que a veces estas referencias pueden llegar por referencia de paquete transitiva y, por tanto, puede ser más difícil de quitar que una referencia directa realizada en el archivo del proyecto. En tales casos, asegúrese de que todas las referencias de paquetes directos usan Visual Studio paquetes del SDK de 2022. Puede hacer referencia a *project.assets.jspara identificar* la cadena de paquetes responsables de incorporar el ensamblado en desuso. Actualizar una referencia de paquete transitivo a Visual Studio versión 2022 es tan fácil como instalarla como una referencia directa.

Si no puede cambiar el árbol de dependencias (por ejemplo, porque implica una dependencia de terceros), puede agregar una referencia de paquete directo al paquete anterior a Visual Studio 2022 y agregar metadatos a ese elemento para resolver el error del `ExcludeAssets="compile"` `PackageReference` compilador. Pero tenga en cuenta que, con esta técnica, la extensión puede conservar una dependencia en un ensamblado anterior a Visual Studio 2022 y es posible que la extensión no funcione correctamente en tiempo de ejecución.

### <a name="missing-reference-to-an-interop-assembly"></a>Falta una referencia a un ensamblado de interoperabilidad

Al hacer referencia a un ensamblado que se compiló con el SDK de Visual Studio 2022, es posible que reciba un error sobre la falta de una referencia de ensamblado.

Error de ejemplo:

> Error CS0012 El tipo "IVsTextViewFilter" se define en un ensamblado al que no se hace referencia. Debe agregar una referencia al ensamblado "Microsoft.VisualStudio.TextManager.Interop, Version=7.1.40304.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"

Con la [tabla de reapping](migrated-assemblies.md)del ensamblado de referencia , puede confirmar que el ensamblado solicitado no es al que debería tener que hacer referencia.

La mejor solución es actualizar la dependencia a una versión compilada con el SDK de Visual Studio 2022 para que el compilador ya no solicite el ensamblado de interoperabilidad quitado.

En algunos casos, ofrecemos un paquete Visual Studio versión 2022 para el ensamblado en desuso que contiene reenviadores de tipos. Cuando esté disponible, tiene la opción de agregar una referencia de paquete a la versión Visual Studio 2022 del paquete obsoleto para que los reenviadores de tipos resuelvan el error del compilador.

### <a name="iasyncserviceprovider-is-missing"></a>`IAsyncServiceProvider` falta

Hay dos definiciones de esta interfaz, en dos espacios de nombres. Solo uno de ellos estaba pensado para el consumo administrado.

Visual Studio espacio de nombres de 2019 | Visual Studio espacio de nombres de 2022 | Uso previsto
--|--|--
Microsoft.VisualStudio.Shell.IAsyncServiceProvider | Microsoft.VisualStudio.Shell.IAsyncServiceProvider | Consumo de código administrado
Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider | Microsoft.VisualStudio.Shell.COMAsyncServiceProvider.IAsyncServiceProvider | solo interoperabilidad de bajo nivel

Si ve un error sobre , puede que esté usando el destinado a `IAsyncServiceProvider` código nativo (la segunda fila). 
Si es así, puede actualizar al nuevo espacio de nombres o cambiar a la interfaz más fácil de administrar.

### <a name="dte-and-_dte-type-cast-failures"></a>`DTE` y `_DTE` errores de conversión de tipos

`DTE` y `_DTE` son interfaces. Una deriva de la otra. Sin embargo, Visual Studio 2022, se intercambian los tipos base y derivado.
Esto hace que se produce un error en determinadas asignaciones o conversión de tipos.

Esto también significa que, cuando solía usar `new DTE()` , ahora debe usar `new _DTE()` .

### <a name="missing-argument-on-a-method-invocation"></a>Falta el argumento en una invocación de método

Algunos métodos ya no declaran argumentos predeterminados para los parámetros opcionales de la API de interoperabilidad.
Si recibe un error sobre un argumento que falta para una llamada de interoperabilidad COM y el parámetro llama a para un tipo, el valor predeterminado anterior que definió la API de interoperabilidad de Visual Studio 2019 puede haber sido , por lo que considere la posibilidad de agregar como argumento para resolver el `object` `""` error de `""` compilación.

Cuando tenga dudas sobre cuál era el argumento predeterminado, intente cambiar el contexto del servicio de lenguaje de Visual Studio 2022 a Visual Studio 2019 para obtener Intellisense con los ensamblados de interoperabilidad anteriores para ver cuál era el argumento predeterminado y, a continuación, agregarlo explícitamente al código. Seguirá funcionando bien cuando se compile para Visual Studio 2019, pero ahora se compilará para Visual Studio 2022.

Corrección de ejemplo:

```diff
-process4.Attach2();
+process4.Attach2("");
```
