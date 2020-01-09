---
title: Solucionar problemas de referencias rotas
ms.date: 03/21/2017
ms.topic: troubleshooting
helpviewer_keywords:
- C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5116d2487ca9f53c460e1cae8f362f3ff1bcdf8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565921"
---
# <a name="troubleshoot-broken-references"></a>Solucionar problemas de referencias rotas

Si la aplicación intenta usar una referencia rota, se genera un error de excepción. La incapacidad de encontrar el componente al que se hace referencia es el desencadenador principal del error, pero hay varias situaciones en las que se puede considerar una referencia como rota. Estas instancias se muestran en la siguiente lista:

- La ruta de acceso de referencia del proyecto es incorrecta o está incompleta.

- Se ha eliminado el archivo al que se hace referencia.

- Se ha cambiado el nombre del archivo al que se hace referencia.

- Se ha producido un error en la conexión de red o en la autenticación.

- Se hace referencia a un componente COM que no está instalado en el equipo.

A continuación se ofrecen soluciones a estos problemas.

> [!NOTE]
> Se hace referencia a los archivos de los ensamblados mediante rutas de acceso absolutas en el archivo del proyecto. Por tanto, es posible que a los usuarios que trabajan en un entorno de varios desarrolladores les falte un ensamblado al que se hace referencia en su entorno local. Para evitar estos errores, en estos casos es mejor agregar referencias entre proyectos. Para más información, vea [Programar con ensamblados](/dotnet/framework/app-domains/programming-with-assemblies).

## <a name="reference-path-is-incorrect"></a>La ruta de acceso de referencia es incorrecta

Si los proyectos se comparten en equipos diferentes, es posible que no se encuentren algunas referencias cuando un componente se encuentra en un directorio diferente en cada equipo. Las referencias se almacenan con el nombre del archivo de componente (por ejemplo, *MyComponent*). Cuando se agrega una referencia a un proyecto, la ubicación de la carpeta del archivo de componente (por ejemplo, *C:\MyComponents*) se anexa a la propiedad del proyecto **ReferencePath**.

Cuando se abre el proyecto, intenta encontrar estos archivos de componente a los que se hace referencia mediante una búsqueda en los directorios de la ruta de acceso de referencia. Si el proyecto se abre en un equipo que almacena el componente en otro directorio, por ejemplo, *D:\MyComponents*, no se puede encontrar la referencia y aparece un error en la **lista de tareas**.

Para corregir este problema, puede eliminar la referencia rota y después reemplazarla mediante el cuadro de diálogo **Agregar referencia**. Otra solución es usar el elemento **Reference Path** (Ruta de acceso de referencia) en las páginas de propiedades del proyecto y modificar las carpetas de la lista para que apunten a las ubicaciones correctas. La propiedad **Reference Path** se guarda para cada usuario en cada equipo. Por tanto, si modifica la ruta de acceso de referencia, esto no afecta a otros usuarios del proyecto.

> [!TIP]
> Las referencias entre proyectos no tienen estos problemas. Por este motivo, úselas en lugar de las referencias de archivo, si es posible.

### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Para reparar una referencia de proyecto rota mediante la corrección de la ruta de acceso de referencia

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el nodo del proyecto y haga clic en **Propiedades**.

   Aparece el **Diseñador de proyectos**.

1. Si usa Visual Basic, seleccione la página **Referencias** y haga clic en el botón **Rutas de acceso de referencia**. En el cuadro de diálogo **Rutas de acceso de referencia**, escriba la ruta de acceso de la carpeta que contiene el elemento al que quiere hacer referencia en el campo **Carpeta** y luego haga clic en el botón **Agregar carpeta**.

    Si usa C#, seleccione la página **Rutas de acceso de referencia**. En el campo **Carpeta**, escriba la ruta de acceso de la carpeta que contiene el elemento al que quiere hacer referencia y luego haga clic en el botón **Agregar carpeta**.

## <a name="referenced-file-has-been-deleted"></a>Se ha eliminado el archivo al que se hace referencia

Es posible que el archivo al que se hace referencia se haya eliminado y ya no exista en la unidad.

### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Para reparar una referencia de proyecto rota de un archivo que ya no existe en la unidad

- Elimine la referencia.

- Si la referencia existe en otra ubicación del equipo, léala desde esa ubicación.

## <a name="referenced-file-has-been-renamed"></a>Se ha cambiado el nombre del archivo al que se hace referencia

Es posible que se haya cambiado el nombre del archivo al que se hace referencia.

### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Para reparar una referencia rota de un archivo al que se le ha cambiado el nombre

- Elimine la referencia y después agregue una referencia al archivo al que se le ha cambiado el nombre.

- Si la referencia existe en otra ubicación del equipo, tiene que leerla desde esa ubicación.

## <a name="network-connection-or-authentication-has-failed"></a>Se ha producido un error en la conexión de red o en la autenticación

Puede haber varias causas por las que no se pueda tener acceso a los archivos, por ejemplo, una conexión de red o una autenticación incorrectas. Cada causa puede tener un único medio de recuperación; por ejemplo, es posible que tenga que ponerse en contacto con el administrador local para acceder a los recursos necesarios. No obstante, siempre hay la opción de eliminar la referencia y corregir el código en el que se usaba esa referencia.

## <a name="com-component-is-not-installed-on-computer"></a>No se ha instalado el componente COM en el equipo

Si un usuario ha agregado una referencia a un componente COM y un segundo usuario intenta ejecutar el código en un equipo que no tenga este componente instalado, el segundo usuario recibirá un error que indica que la referencia está rota. Si se instala el componente en el segundo equipo, se corregirá el error. Para obtener más información sobre cómo usar referencias a componentes COM en los proyectos, consulte [Interoperabilidad COM en aplicaciones .NET Framework](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications).

## <a name="see-also"></a>Vea también

- [Página Referencias, Diseñador de proyectos (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)
