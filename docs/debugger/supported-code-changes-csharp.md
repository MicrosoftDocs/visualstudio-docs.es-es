---
title: Cambios de código admitidos (C# y Visual Basic) | Microsoft Docs
ms.date: 10/11/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], supported code changes
- Edit and Continue [Visual Basic], supported code changes
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 44881035da14483c3ddf1f4c48cb3957a1ce8b50
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729086"
---
# <a name="supported-code-changes-c-and-visual-basic"></a>Cambios de código admitidos (C# y Visual Basic)
Editar y continuar controla la mayoría de los tipos de cambios de código dentro de los cuerpos de método. Ahora bien, durante la depuración, no es posible efectuar la mayoría de cambios fuera de los cuerpos de método y algunos cambios dentro de estos. Para efectuar dichos cambios no compatibles, es necesario detener la depuración y reiniciar con una versión nueva del código.

## <a name="supported-changes-to-code"></a>Cambios admitidos en el código

En la tabla siguiente se muestran los cambios que se pueden C# realizar y Visual Basic código durante una sesión de depuración sin reiniciar la sesión.

|Elemento o característica de lenguaje|Operación de edición admitida|Limitaciones|
|-|-|-|
|Tipos|Agregar métodos, campos, constructores, et al|[Sí](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Iterators|Agregar o modificar|No|
|Expresiones Async/Await|Agregar o modificar|[Sí](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Objetos dinámicos|Agregar o modificar|No|
|expresiones lambda|Agregar o modificar|[Sí](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|
|Expresiones LINQ|Agregar o modificar|[Igual que las expresiones lambda](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits)|

> [!NOTE]
> Las características de lenguaje más recientes, como la interpolación de cadenas y los operadores condicionales null, se admiten generalmente mediante editar y continuar. Para obtener la información más reciente, consulte la página [ediciones compatibles con ENC](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits) .

## <a name="unsupported-changes-to-code"></a>Cambios no admitidos en el código
 Los siguientes cambios no se pueden aplicar C# a y Visual Basic código durante una sesión de depuración:

- Cambios en la instrucción actual o en cualquier otra instrucción activa.

     Entre las instrucciones activas se incluye cualquier instrucción, en funciones de la pila de llamadas, que haya sido llamada para llegar a la instrucción actual.

     Un fondo amarillo marca la instrucción actual en la ventana de código fuente. Un fondo sombreado marca otras instrucciones activas; son de solo lectura. Estos colores predeterminados se pueden cambiar en el cuadro de diálogo **Opciones**.

- En la tabla siguiente se muestran los cambios no admitidos en el código mediante el elemento de lenguaje.

|Elemento o característica de lenguaje|Operación de edición no admitida|
|-|-|
|Todos los elementos de código|Cambiar nombre|
|Espacios de nombres|Agregar|
|Espacios de nombres, tipos, miembros|Eliminar|
|Genéricos|Agregar o modificar|
|Interfaces|Modificar|
|Tipos|Agregar un miembro abstracto o virtual, agregar invalidación (ver [detalles](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Tipos|Agregar destructor|
|Miembros|Modificar un miembro que hace referencia a un tipo de interoperabilidad incrustado|
|Miembros|Modificar un miembro estático una vez que ya se ha accedido mediante la ejecución de código|
|Miembros (Visual Basic)|Modificar un miembro con on error o resume (instrucción)|
|Miembros (Visual Basic)|Modificar un miembro que contenga una cláusula Aggregate, Group by, simple join o Group join LINQ|
|Métodos|Modificar firmas|
|Métodos|Convertir un método Abstract en no abstracto agregando un cuerpo de método|
|Métodos|Eliminar cuerpo del método|
|Atributos|Agregar o modificar|
|Eventos o propiedades|Modificar un parámetro de tipo, tipo base, tipo de delegado o tipo de valor devuelto |
|Operadores o indizadores|Modificar un parámetro de tipo, tipo base, tipo de delegado o tipo de valor devuelto |
|bloques catch|Modificar cuando contiene una instrucción activa|
|bloques try-catch-finally|Modificar cuando contiene una instrucción activa|
|Using (instrucciones)|Agregar|
|métodos Async/lambdas|Modificar un método o una expresión lambda asincrónica en un proyecto destinado a .NET Framework 4 y versiones inferiores (vea los [detalles](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|
|Iterators|Modificar un iterador en un proyecto destinado a .NET Framework 4 y versiones inferiores (vea los [detalles](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))|

## <a name="unsafe-code"></a>Código no seguro
 Los cambios efectuados en el código no seguro tienen las mismas limitaciones que los cambios efectuados en el código seguro, con una restricción adicional: Editar y continuar no admite cambios en el código no seguro que esté dentro de un método que contenga el operador `stackalloc`.

## <a name="unsupported-app-scenarios"></a>Escenarios de aplicaciones no admitidos

Las aplicaciones y plataformas no compatibles incluyen ASP.NET 5, Silverlight 5 y Windows 8.1.

> [!NOTE]
> Entre las aplicaciones que se admiten se incluyen UWP en Windows 10 y aplicaciones x86 y x64 que tienen como destino el escritorio .NET Framework 4,6 o versiones posteriores (el .NET Framework es solo una versión de escritorio).

## <a name="unsupported-scenarios"></a>Escenarios no admitidos
 La opción Editar y continuar no se encuentra disponible en los siguientes escenarios de depuración:

- Depuración en modo mixto (nativa o administrada).

- Depuración de SQL.

- Depuración de un volcado de Dr. Watson.

- Depuración de una aplicación incrustada en tiempo de ejecución.

- Depurar una aplicación mediante asociar al proceso (**Depurar > adjuntar al proceso**) en lugar de ejecutar la aplicación eligiendo **iniciar** en el menú **depurar** .

- Depuración de código optimizado.

- Depurar una versión anterior del código cuando no ha sido posible generar una nueva versión debido a errores de compilación.

## <a name="see-also"></a>Vea también
- [Editar y continuar (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
- [Cómo: Usar Editar y continuar (C#)](../debugger/how-to-use-edit-and-continue-csharp.md)