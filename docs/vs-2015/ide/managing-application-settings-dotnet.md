---
title: Administrar la configuración de la aplicación (.NET) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- msvse_settingsdesigner.err.nameblank
helpviewer_keywords:
- application settings [Visual Studio]
ms.assetid: 35254321-ad14-47d9-b8c6-39ab3203c5d9
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a2d5d5ff514752234bba3020927716d57ee413d1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793291"
---
# <a name="managing-application-settings-net"></a>Administrar la configuración de la aplicación (.NET)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La configuración de la aplicación permite almacenar la información de la aplicación de forma dinámica. La configuración también le permite almacenar información en el equipo cliente que no se debe incluir en el código de la aplicación (por ejemplo, una cadena de conexión), las preferencias del usuario y otra información necesaria en tiempo de ejecución.  
  
 La configuración de la aplicación reemplaza a las propiedades dinámicas que se usaban en versiones anteriores de Visual Studio.  
  
 Cada valor de la aplicación debe tener un nombre único. El nombre puede ser cualquier combinación de caracteres de letras, números o subrayado que no comience por un número ni contenga espacios. Se puede cambiar el nombre mediante la propiedad `Name` .  
  
 La configuración de la aplicación se puede almacenar como cualquier tipo de datos que se pueda serializar en XML o que tenga un `TypeConverter` que implemente `ToString`/`FromString`. Los tipos más comunes son `String`, `Integer`y `Boolean`, pero también puede almacenar valores como <xref:System.Drawing.Color>, <xref:System.Object>, o bien como una cadena de conexión.  
  
 La configuración de la aplicación también contiene un valor. El valor se establece mediante la propiedad **Value** y debe coincidir con el tipo de datos de la configuración.  
  
 Además, la configuración de la aplicación se puede enlazar a una propiedad de un formulario o de un control en tiempo de diseño.  
  
 Hay dos tipos de configuración de la aplicación, en función del ámbito:  
  
- La configuración de ámbito de aplicación se puede utilizar para obtener información como una dirección URL para un servicio Web o una cadena de conexión a bases de datos. Estos valores están asociados a la aplicación. Por consiguiente, los usuarios no pueden cambiarlos en tiempo de ejecución.  
  
- La configuración de ámbito de usuario se puede utilizar para obtener información, como conservar la última posición de un formulario o una preferencia de fuente. Los usuarios pueden modificar estos valores en tiempo de ejecución.  
  
  Puede cambiar el tipo de una configuración con la propiedad **Scope** .  
  
  El sistema del proyecto almacena la configuración de la aplicación en dos archivos XML: un archivo .app.config, que se crea en tiempo de diseño cuando se crea la primera configuración de la aplicación, y un archivo .user.config, que se crea en tiempo de ejecución cuando el usuario que ejecuta la aplicación cambia el valor de parte de la configuración de usuario. Observe que los cambios en la configuración de usuario no se escriben en el disco a menos que la aplicación llame específicamente a un método para que lo haga.  
  
## <a name="creating-application-settings-at-design-time"></a>Crear la configuración de la aplicación en tiempo de diseño  
 En tiempo de diseño, hay dos maneras de crear la configuración de la aplicación: mediante la página **Configuración** del **Diseñador de proyectos**o desde la ventana **Propiedades** de un formulario o un control, lo que le permite enlazar una configuración a una propiedad.  
  
 Cuando crea una configuración con ámbito de aplicación (por ejemplo, una cadena de conexión a bases de datos o una referencia a los recursos del servidor), [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] la guarda en un archivo app.config con la etiqueta `<applicationSettings>` . (Las cadenas de conexión se guardan en la etiqueta `<connectionStrings>` .)  
  
 Cuando crea una configuración con ámbito de usuario (por ejemplo, fuente predeterminada, página principal o tamaño de la ventana), [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] la guarda en un archivo app.config con la etiqueta `<userSettings>` .  
  
> [!IMPORTANT]
>  Si almacena cadenas de conexión en .app.config, debe tomar precauciones para evitar revelar información confidencial en la cadena de conexión, como contraseñas o rutas de acceso al servidor.  
>   
>  Si toma la información de la cadena de conexión de un origen externo (un usuario que suministre un Id. de usuario y una contraseña, por ejemplo), debe asegurarse de que los valores que utilice para crear la cadena de conexión no contengan parámetros adicionales que modifiquen el comportamiento de la conexión.  
>   
>  Plantéese utilizar la característica de configuración protegida para cifrar información confidencial en el archivo de configuración. Para obtener más información, vea [Proteger la información de conexión](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
> [!NOTE]
>  Dado que no hay ningún modelo del archivo de configuración para las bibliotecas de clases, la configuración de la aplicación no se aplica a los proyectos de la biblioteca de clases. La excepción es un proyecto de archivo DLL de Visual Studio Tools para Office, que puede tener un archivo de configuración.  
  
## <a name="using-customized-settings-files"></a>Usar archivos de configuración personalizados  
 Puede agregar archivos de configuración personalizados a su proyecto para facilitar la administración de grupos de opciones de configuración. La configuración contenida en un mismo archivo se carga y guarda como una unidad. Por consiguiente, poder almacenar configuraciones en distintos archivos correspondientes a los grupos utilizados con frecuencia y poco utilizados puede ahorrar tiempo al cargar y guardar configuraciones.  
  
 Por ejemplo, puede agregar un archivo a su proyecto como SpecialSettings.settings. Aunque su clase `SpecialSettings` no se exponga en el espacio de nombres `My` , **Ver código** puede leer el archivo de configuración personalizado que contiene `Partial Class SpecialSettings`.  
  
 El Diseñador de configuración busca primero el archivo Settings.settings creado por el sistema del proyecto; éste es el archivo que muestra de manera predeterminada el Diseñador de configuración en la ficha **Configuración** . Settings.settings se encuentra en la carpeta My Project para los proyectos de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] y en la carpeta Propiedades para los proyectos de [!INCLUDE[csprcs](../includes/csprcs-md.md)] . A continuación, el Diseñador de proyectos busca otros archivos de configuración en la carpeta raíz del proyecto. Por consiguiente, debe colocar en ella el archivo de configuración personalizado. Si agrega un archivo .settings en otra ubicación del proyecto, el Diseñador de proyectos no lo encontrará.  
  
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-basic"></a>Obtener acceso o cambiar la configuración de la aplicación en tiempo de ejecución en Visual Basic  
 En los proyectos de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , puede obtener acceso a la configuración de la aplicación en tiempo de ejecución por medio del objeto `My.Settings` . En la página **Configuración** , haga clic en el botón **Ver código** con el fin de ver el archivo Settings.vb. Settings.vb define la clase `Settings` , que le permite controlar estos eventos en la clase de configuración: <xref:System.Configuration.ApplicationSettingsBase.SettingChanging>, <xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>, <xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>y <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>. Tenga en cuenta que la clase `Settings` de Settings.vb es una clase parcial, que muestra solamente el código que tiene el usuario, no toda la clase generada. Para obtener más información sobre cómo tener acceso a la configuración de la aplicación mediante el objeto `My.Settings` , vea [Accessing Application Settings](http://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e).  
  
 Los valores de configuración de ámbito de usuario que el usuario cambia en tiempo de ejecución (por ejemplo, la posición de un formulario) se almacenan en un archivo user.config. Observe que los valores predeterminados se siguen guardando en app.config.  
  
 Si ha cambiado parte de la configuración de ámbito de usuario durante el tiempo de ejecución, por ejemplo, al probar la aplicación, y desea restablecer esta configuración a sus valores predeterminados, haga clic en el botón **Sincronizar** .  
  
 Recomendamos encarecidamente utilizar el objeto `My.Settings` y el archivo .settings predeterminado para tener acceso a las configuraciones. Esto se debe a que puede utilizar el Diseñador de configuración para asignar propiedades a los valores, y, además, la configuración del usuario se guarda automáticamente antes de cerrar la aplicación. Sin embargo, su aplicación de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] puede obtener acceso directamente a la configuración. En ese caso, necesita tener acceso a la clase `MySettings` y utilizar un archivo .settings personalizado en la raíz del proyecto. También debe guardar la configuración del usuario antes de finalizar la aplicación, igual que con una aplicación de C#; esto se describe en la sección siguiente.  
  
## <a name="accessing-or-changing-application-settings-at-run-time-in-visual-c"></a>Obtener acceso o cambiar la configuración de la aplicación en tiempo de ejecución en Visual C#  
 En otros lenguajes distintos de [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], como [!INCLUDE[csprcs](../includes/csprcs-md.md)], se debe tener acceso directamente a la clase `Settings` , como se muestra en el siguiente ejemplo de [!INCLUDE[csprcs](../includes/csprcs-md.md)] .  
  
```csharp  
Properties.Settings.Default.FirstUserSetting = "abc";  
```  
  
 También debe llamar explícitamente al método `Save` de esta clase contenedora para conservar la configuración del usuario. Esto normalmente se realiza en el controlador de eventos `Closing` del formulario principal. En el ejemplo siguiente de [!INCLUDE[csprcs](../includes/csprcs-md.md)] , se muestra una llamada al método `Save` .  
  
```csharp  
Properties.Settings.Default.Save();  
```  
  
 Para obtener información general sobre cómo obtener acceso a la configuración de la aplicación a través de la clase `Settings`, vea [Introducción a la configuración de la aplicación](http://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc). Para obtener información sobre cómo recorrer en iteración la configuración, vea este [artículo del foro](http://social.msdn.microsoft.com/Forums/vstudio/40fbb470-f1e8-4a02-a4a0-9f62b54d0fc4/is-this-possible-propertiessettingsdefault?forum=csharpgeneral).  
  
## <a name="see-also"></a>Vea también  
 [Acceso a la configuración de la aplicación](http://msdn.microsoft.com/library/e38d0cc7-247a-46ca-ba04-f2913f0adb2e)
