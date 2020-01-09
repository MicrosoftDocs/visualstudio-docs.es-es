---
title: Página Configuración, Diseñador de proyectos
ms.date: 06/14/2018
ms.topic: reference
f1_keywords:
- ApplicationSettingsOverview
helpviewer_keywords:
- Settings page in Project Designer
- Project Designer, Settings page
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f4ca1def334241999445e3f11cf142aa426d962
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566779"
---
# <a name="settings-page-project-designer"></a>Página Configuración, Diseñador de proyectos

Use la página **Configuración** del Diseñador de proyectos para especificar la configuración de la aplicación de un proyecto. La configuración de la aplicación permite almacenar y recuperar valores de propiedad y otros datos para la aplicación de forma dinámica. También permite mantener la aplicación y las preferencias del usuario personalizadas en un equipo cliente. Para obtener más información, vea [Administración de la configuración de la aplicación](../managing-application-settings-dotnet.md).

Para acceder a la página **Configuración**, seleccione un nodo de proyecto en el **Explorador de soluciones** y, luego, seleccione **Proyecto** > **Propiedades**. Cuando aparezca el Diseñador de proyectos, seleccione la pestaña **Configuración**.

## <a name="header-bar"></a>Barra de encabezado

La barra de encabezado de la parte superior de la página **Configuración** contiene varios controles:

**Sincronizar**

**Sincronizar** restaura la configuración con ámbito de usuario que usa la aplicación en tiempo de ejecución o durante la depuración a sus valores predeterminados, tal como se define en tiempo de diseño. Para restaurar los datos, quite los archivos específicos de la aplicación generados en tiempo de ejecución del disco, pero no de los datos del proyecto.

**Cargar configuración web**

**Cargar configuración web** muestra un cuadro de diálogo **Iniciar sesión** que permite cargar la configuración para un usuario autenticado o para usuarios anónimos. Este botón se habilita solo cuando se han habilitado los servicios de aplicación cliente en la página **Servicios** y se ha especificado una **Ubicación del servicio de configuración web**.

**Vista Código**

Para proyectos de C#, el botón **Vista Código** permite ver el código en el archivo *Settings.cs*. Este archivo define la clase `Settings`, lo que permite controlar eventos específicos en el objeto `Settings`. En los lenguajes que no sean Visual Basic, debe llamar explícitamente al método `Save` de esta clase contenedora para conservar la configuración del usuario. Esto normalmente se realiza en el controlador de eventos **Cerrando** del formulario principal. Lo siguiente es un ejemplo de una llamada al método `Save`:

```csharp
Properties.Settings.Default.Save();
```

Para proyectos de Visual Basic, el botón **Vista Código** permite ver el código en el archivo *Settings.vb*. Este archivo define la clase `MySettings`, lo que permite controlar eventos específicos en el objeto `My.Settings`. Para obtener más información sobre cómo tener acceso a la configuración de la aplicación mediante el objeto `My.Settings`, vea [Acceso a la configuración de la aplicación](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Para obtener más información sobre el acceso a la configuración de la aplicación, vea [Configuración de la aplicación en formularios Windows Forms](/dotnet/framework/winforms/advanced/application-settings-for-windows-forms).

**Modificador de acceso**

El botón **Modificador de acceso** especifica el nivel de acceso de las clases del asistente `Properties.Settings` (en C#) o `My.Settings` (en Visual Basic) que Visual Studio genera en *Settings.Designer.cs* o *Settings.Designer.vb*.

Para proyectos de Visual C#, el modificador de acceso puede ser **Interno** o **Público**.

Para proyectos de Visual Basic, el modificador de acceso puede ser **Amigo** o **Público**.

De forma predeterminada, el valor es **Interno** en C# y **Amigo** en Visual Basic. Cuando Visual Studio genera clases del asistente como **Interno** o **Amigo**, las aplicaciones ejecutables ( *.exe*) no pueden acceder a los recursos y la configuración que ha agregado a las bibliotecas de clases (archivos *.dll*). Si tiene que compartir recursos y la configuración de una biblioteca de clases, establezca el modificador de acceso en **Público**.

Para obtener más información sobre las clases del asistente de configuración, vea [Administración de la configuración de la aplicación](../managing-application-settings-dotnet.md).

## <a name="settings-grid"></a>Cuadrícula Configuración

La **cuadrícula Configuración** se usa para configurar la configuración de la aplicación. Esta cuadrícula incluye las siguientes columnas:

**Name**

Escriba el nombre de la configuración de la aplicación en este campo.

**Type**

Use la lista desplegable para seleccionar un tipo de configuración. Los tipos utilizados con mayor frecuencia aparecen en la lista desplegable, por ejemplo, **Cadena**, **(Cadena de conexión)** y **System.Drawing.Font**. Puede elegir otro tipo si hace clic en **Examinar** al final de la lista y elige un tipo en el cuadro de diálogo **Select a Type** (Seleccionar un tipo). Después de elegir un tipo, este se agrega a los tipos comunes en la lista desplegable (solo para la solución actual).

**Ámbito**

Seleccione **Aplicación** o **Usuario**.

La configuración de ámbito de la aplicación, como las cadenas de conexión, está asociada con la aplicación. Los usuarios no pueden cambiar la configuración de ámbito de la aplicación en tiempo de ejecución.

La configuración de ámbito de usuario, como las fuentes del sistema, está diseñada para usarse en las preferencias del usuario. Los usuarios pueden cambiarla en tiempo de ejecución.

**Valor**

Los datos o el valor asociado con la configuración de la aplicación. Por ejemplo, si el valor es una fuente, su valor podría ser **Verdana, 9.75pt, style=Bold**.

## <a name="see-also"></a>Vea también

- [Administración de la configuración de la aplicación](../managing-application-settings-dotnet.md)
- [Acceso a la configuración de la aplicación (Visual Basic)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
