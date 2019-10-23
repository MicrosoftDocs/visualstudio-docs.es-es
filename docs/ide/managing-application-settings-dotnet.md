---
title: Administración de la configuración de la aplicación (.NET)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae4215987ee0a61935efe27ab927d826cc1c6ff9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654631"
---
# <a name="manage-application-settings-net"></a>Administración de la configuración de la aplicación (.NET)

La configuración de la aplicación permite almacenar la información de la aplicación de forma dinámica. La configuración también permite almacenar información en el equipo cliente que no se debe incluir en el código de la aplicación (por ejemplo, una cadena de conexión), las preferencias del usuario y otra información necesaria en tiempo de ejecución.

La configuración de la aplicación reemplaza a las propiedades dinámicas que se usaban en versiones anteriores de Visual Studio.

Cada valor de la aplicación debe tener un nombre único. El nombre puede ser cualquier combinación de letras, números o caracteres de subrayado que no comience por un número ni contenga espacios. Se puede cambiar mediante la propiedad `Name`.

La configuración de la aplicación se puede almacenar como cualquier tipo de datos que se pueda serializar en XML o que tenga un elemento `TypeConverter` que implemente `ToString`/`FromString`. Los tipos más comunes son `String`, `Integer`y `Boolean`, pero también puede almacenar valores como <xref:System.Drawing.Color>, <xref:System.Object>, o bien como una cadena de conexión.

La configuración de la aplicación también contiene un valor. El valor se establece mediante la propiedad **Value** y debe coincidir con el tipo de datos de la configuración.

Además, la configuración de la aplicación se puede enlazar a una propiedad de un formulario o de un control en tiempo de diseño.

Hay dos tipos de configuración de la aplicación, en función del ámbito:

- La configuración de ámbito de aplicación se puede utilizar para obtener información, por ejemplo, una dirección URL para un servicio web o una cadena de conexión a bases de datos. Estos valores están asociados a la aplicación. Por consiguiente, los usuarios no pueden cambiarlos en tiempo de ejecución.

- La configuración de ámbito de usuario se puede utilizar para obtener información, como conservar la última posición de un formulario o una preferencia de fuente. Los usuarios pueden modificar estos valores en tiempo de ejecución.

Puede cambiar el tipo de una configuración con la propiedad **Scope** .

El sistema del proyecto almacena la configuración de la aplicación en dos archivos XML:

- un archivo *app.config*, que se crea en tiempo de diseño cuando se crea la primera configuración de la aplicación

- un archivo *user.config*, que se crea en tiempo de ejecución cuando el usuario que ejecuta la aplicación cambia el valor de cualquier configuración de usuario.

Observe que los cambios en la configuración de usuario no se escriben en el disco a menos que la aplicación llame específicamente a un método para que lo haga.

## <a name="create-application-settings-at-design-time"></a>Creación de la configuración de la aplicación en tiempo de diseño

En tiempo de diseño, hay dos maneras de crear la configuración de la aplicación: mediante la página **Configuración** del **Diseñador de proyectos**o desde la ventana **Propiedades** de un formulario o un control, lo que le permite enlazar una configuración a una propiedad.

Cuando se crea una configuración con ámbito de aplicación (por ejemplo, una cadena de conexión de base de datos o una referencia a recursos del servidor), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la guarda en un archivo *app.config* con la etiqueta `<applicationSettings>`. (Las cadenas de conexión se guardan en la etiqueta `<connectionStrings>` .)

Cuando se crea una configuración con ámbito de usuario (por ejemplo, fuente predeterminada, página principal o tamaño de ventana), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la guarda en un archivo *app.config* con la etiqueta `<userSettings>`.

> [!IMPORTANT]
> Si almacena cadenas de conexión en *app.config*, debe tomar precauciones para evitar revelar información confidencial en la cadena de conexión, como contraseñas o rutas de acceso al servidor.
>
> Si toma la información de la cadena de conexión de un origen externo (un usuario que suministre un Id. de usuario y una contraseña, por ejemplo), debe asegurarse de que los valores que utilice para crear la cadena de conexión no contengan parámetros adicionales que modifiquen el comportamiento de la conexión.
>
> Plantéese utilizar la característica de configuración protegida para cifrar información confidencial en el archivo de configuración. Para obtener más información, vea [Proteger la información de conexión](/dotnet/framework/data/adonet/protecting-connection-information).

> [!NOTE]
> Dado que no hay ningún modelo del archivo de configuración para las bibliotecas de clases, la configuración de la aplicación no se aplica a los proyectos de la biblioteca de clases. La excepción es un proyecto de archivo DLL de Visual Studio Tools para Office, que puede tener un archivo de configuración.

## <a name="use-customized-settings-files"></a>Uso de archivos de configuración personalizados

Puede agregar archivos de configuración personalizados a su proyecto para facilitar la administración de grupos de opciones de configuración. La configuración contenida en un mismo archivo se carga y guarda como una unidad. El almacenamiento de configuraciones en distintos archivos correspondientes a los grupos usados con frecuencia y poco usados puede ahorrar tiempo al cargar y guardar configuraciones.

Por ejemplo, puede agregar un archivo como *SpecialSettings.settings* al proyecto. Aunque su clase `SpecialSettings` no se exponga en el espacio de nombres `My` , **Ver código** puede leer el archivo de configuración personalizado que contiene `Partial Class SpecialSettings`.

El **Diseñador de configuración** primero busca el archivo *Settings.settings* creado por el sistema del proyecto; es el archivo predeterminado que muestra el **Diseñador de configuración** en la pestaña **Configuración**. *Settings.settings* se encuentra en la carpeta *Mi proyecto* para los proyectos de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] y en la carpeta *Propiedades* para los proyectos de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]. Luego el **Diseñador de proyectos** busca otros archivos de configuración en la carpeta raíz del proyecto. Por consiguiente, debe colocar en ella el archivo de configuración personalizado. Si agrega un archivo *.settings* en otra ubicación del proyecto, el **Diseñador de proyectos** no lo encontrará.

## <a name="access-or-change-application-settings-at-run-time-in-visual-basic"></a>Acceso a la configuración de la aplicación o modificación de ella en tiempo de ejecución en Visual Basic

En los proyectos de Visual Basic, puede obtener acceso a la configuración de la aplicación en tiempo de ejecución por medio del objeto `My.Settings`. En la página **Configuración**, haga clic en el botón **Ver código** para ver el archivo *Settings.vb*. *Settings.vb* define la clase `Settings`, que permite controlar estos eventos en la clase de configuración: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded> y <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. Tenga en cuenta que la clase `Settings` de *Settings.vb* es una clase parcial que muestra solamente el código que tiene el usuario, no toda la clase generada. Para obtener más información sobre cómo acceder a la configuración de la aplicación mediante el objeto `My.Settings`, vea [Acceso a la configuración de la aplicación (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings).

Los valores de configuración de ámbito de usuario que el usuario cambia en tiempo de ejecución (por ejemplo, la posición de un formulario) se almacenan en un archivo *user.config*. Observe que los valores predeterminados se siguen guardando en *app.config*.

Si ha cambiado parte de la configuración de ámbito de usuario durante el tiempo de ejecución, por ejemplo, al probar la aplicación, y quiere restablecer esta configuración a sus valores predeterminados, haga clic en el botón **Sincronizar**.

Se recomienda encarecidamente usar el objeto `My.Settings` y el archivo *.settings* predeterminado para acceder a la configuración. Esto se debe a que puede usar el **Diseñador de configuración** para asignar propiedades a la configuración y, además, la configuración del usuario se guarda automáticamente antes de cerrar la aplicación. Pero la aplicación de Visual Basic puede obtener acceso directamente a la configuración. En ese caso, necesita acceso a la clase `MySettings` y usar un archivo *.settings* personalizado en la raíz del proyecto. Debe guardar la configuración del usuario antes de finalizar la aplicación, igual que con una aplicación de C#; esto se explica en la sección siguiente.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="access-or-change-application-settings-at-run-time-in-c"></a>Acceso a la configuración de la aplicación o modificación de ella en tiempo de ejecución en C#
<!-- markdownlint-enable MD003 MD020 -->

En otros lenguajes distintos de Visual Basic, como C#, se debe tener acceso directamente a la clase `Settings`, como se muestra en el ejemplo de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] siguiente.

```csharp
Properties.Settings.Default.FirstUserSetting = "abc";
```

Debe llamar explícitamente al método `Save` de esta clase contenedora para conservar la configuración del usuario. Esto normalmente se realiza en el controlador de eventos `Closing` del formulario principal. En el ejemplo siguiente de C#, se muestra una llamada al método `Save`.

```csharp
Properties.Settings.Default.Save();
```

Para obtener información general sobre cómo acceder a la configuración de la aplicación mediante la clase `Settings`, vea [Introducción a la configuración de la aplicación (.NET Framework)](/dotnet/framework/winforms/advanced/application-settings-overview). Para obtener información sobre cómo recorrer en iteración la configuración, vea este [artículo del foro](https://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).

## <a name="see-also"></a>Vea también

- [Acceso a la configuración de la aplicación (.NET Framework)](/dotnet/visual-basic/developing-apps/programming/app-settings/accessing-application-settings)
