---
title: "Usar p&#225;ginas de opciones | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "páginas de opciones de herramientas [SDK de Visual Studio], uso"
ms.assetid: 5ae6b995-3aeb-43a7-9786-4cf69faa101c
caps.latest.revision: 36
caps.handback.revision: 36
manager: "douge"
---
# Usar p&#225;ginas de opciones
El modelo de automatización de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proporciona el objeto <xref:EnvDTE.DTE> para permitir que los paquetes VSPackage tengan acceso al cuadro de diálogo **Opciones** del menú **Herramientas**.  
  
 Normalmente, se puede acceder a las páginas del cuadro de diálogo **Opciones** mediante el modelo de automatización, ya sea si las páginas son proporcionadas por el entorno de desarrollo integrado \(IDE\) de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o por un paquete VSPackage. Sin embargo, existen las excepciones siguientes:  
  
-   No se puede obtener acceso mediante programación a la configuración de la página **Ayuda dinámica**. La característica **Ayuda dinámica** se controla mediante el modelo de automatización, pero el control debe realizarse directamente en el código. Para obtener más información, consulte [How to: Control the Dynamic Help Window](http://msdn.microsoft.com/es-es/7f5777aa-c270-4058-a175-8ce8a4ed25eb).  
  
-   El control de la configuración de la página **Fuentes y colores** se proporciona a través de su propia API, no a través del modelo de automatización. Para obtener más información, consulte [Utilizar fuentes y colores](../extensibility/using-fonts-and-colors.md).  
  
-   Las propiedades específicas del lenguaje no se pueden obtener a través del modelo de automatización.  
  
 Las páginas **Opciones** que no admiten el modelo de automatización de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] no pueden devolver una colección <xref:EnvDTE.Properties> de automatización cuando se las consulta. Si se devuelve la colección, no figuran todas las características. Para obtener más información sobre cómo administrar estas características, vea [Colecciones de propiedades de DTE](../Topic/DTE%20Properties%20Collections.md).  
  
## Administrar páginas de opciones  
 Para administrar páginas **Opciones**, un paquete VSPackage debe obtener un objeto <xref:EnvDTE.DTE> del modelo de automatización.  
  
> [!NOTE]
>  Cuando un paquete VSPackage usa el modelo de automatización para la consultar y cambiar la configuración de páginas de **opciones** instaladas, no extiende las funciones del IDE. Por lo tanto, el paquete no debe implementar un objeto de automatización.  
  
 Para obtener un objeto <xref:EnvDTE.DTE> a través del modelo de automatización, llame al método <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> y proporcione un argumento de id. de servicio de tipo `SID_SDTE` y un argumento de interfaz de tipo `IID__DTE`, como se muestra a continuación.  
  
```  
pServiceProvider->QueryService(SID_SDTE, IID__DTE, (LPVOID*)pDTE);  
```  
  
 Para obtener un objeto <xref:EnvDTE.DTE> mediante el uso de Managed Package Framework \(MPF\), llame al método <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> y proporcione un parámetro `serviceType` de tipo <xref:Microsoft.VisualStudio.Shell.Interop.SDTE>.  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#01](../extensibility/internals/codesnippet/CSharp/using-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#01](../extensibility/internals/codesnippet/VisualBasic/using-options-pages_1.vb)]  
  
 Una página **Opciones** se especifica mediante dos identificadores. El primer identificador es una cadena que indica la carpeta que contiene la página **Opciones**. El segundo identificador es una cadena que indica el elemento específico de esa carpeta. Estos se conocen como categoría y subcategoría de una página de **opciones** o su tema y subtema.  
  
 Por ejemplo, la configuración del editor de texto para controlar el código básico está en el panel de navegación como el miembro **Básico** de la carpeta **Editor de texto**. El identificador de la categoría es `TextEditor` y su subcategoría es `Basic` y se hace referencia a la página **Opciones** en sí como la página `TextEditor.Basic`.  
  
> [!NOTE]
>  Por cuestiones de localización y otras razones, los nombres que se muestran en la página **Opciones** pueden diferir de las cadenas que se usan como identificadores de categoría y subcategoría. Tal vez sea necesario usar la automatización para consultar el IDE y obtener los identificadores correctos, si no están documentados en otro lugar. La ubicación del Registro es HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<VersiónDeVS\>*\\AutomationProperties, donde *\<VersiónDeVS\>* es el número de versión de la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulte [Registro de páginas de opciones personalizadas](../misc/registering-custom-options-pages.md).  
  
 Puede obtener las propiedades de la página `TextEditor.Basic` a través del modelo de automatización si usa el siguiente ejemplo.  
  
```  
CComPtr<_DTE> srpDTE; CComPtr<Properties> srpDTEPropertiesList; hr = srpDTE->get_Properties("TextEditor", "Basic", &srpDTEPropertiesList);  
```  
  
 Para obtener las propiedades mediante MPF, use el método <xref:EnvDTE._DTE.Properties%2A>.  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#02](../extensibility/internals/codesnippet/CSharp/using-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#02](../extensibility/internals/codesnippet/VisualBasic/using-options-pages_2.vb)]  
  
 El método <xref:EnvDTE.Properties.Item%2A> devuelve los valores de configuración individuales de la colección <xref:EnvDTE.Properties> como un objeto <xref:EnvDTE.Property>.  
  
 Al igual que con las categorías y las subcategorías, cada valor de configuración tiene un identificador que es una cadena única. Por ejemplo, la configuración de **Tamaño de tabulación** en la página `TextEditor.Basic` está identificada por la cadena `TabSize`.  
  
> [!NOTE]
>  Por cuestiones de localización y otras razones, los nombres que se muestran en la página **Opciones** pueden diferir de las cadenas que se usan como identificadores de valor de configuración. Tal vez sea necesario usar la automatización para consultar el IDE y obtener los identificadores correctos, si no están documentados en otro lugar.  
  
 Se puede usar el <xref:EnvDTE.Property.Value%2A> del objeto <xref:EnvDTE.Property> devuelto por el método <xref:EnvDTE.Properties.Item%2A> de la colección <xref:EnvDTE.Properties> para consultar y cambiar el estado de configuración.  
  
 Por ejemplo, para establecer el valor de **Tamaño de tabulación** en la página `TextEditor.Basic` a través del modelo de automatización, use el objeto <xref:EnvDTE.Properties> que se devuelve en el ejemplo a continuación.  
  
```  
CComPtr<Property> srpProperty; hr = srpDTEPropertiesList->Item("TabSize", &srpProperty); hr= srpProperty.set_Value(4);  
```  
  
 En este ejemplo se muestra cómo actualizar el valor de **Tamaño de tabulación** mediante MPF.  
  
 [!code-cs[UI_UserSettings_ToolsOptionPages#03](../extensibility/internals/codesnippet/CSharp/using-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#03](../extensibility/internals/codesnippet/VisualBasic/using-options-pages_3.vb)]  
  
 Para obtener más información, consulte [Controlar la configuración de opciones](../Topic/Controlling%20Options%20Settings.md).  
  
## Conservar la configuración de la página de opciones  
 El IDE implementa la persistencia de estado de las páginas de **opciones** que son totalmente compatibles con el modelo de automatización de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 La configuración de las páginas que se incluyen en el IDE se guarda \(o se recupera\) automáticamente cuando un usuario hace clic en el comando **Importar y exportar configuración** en el menú **Herramientas**.  
  
 Puede habilitar su página **Opciones** personalizada para que use esta compatibilidad con la persistencia automática si agrega el indicador `ProfileSave` a la entrada del Registro personalizada de la página **Opciones** en HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\<Versión de VS\>*\\AutomationProperties, donde *\<Versión de VS\>* es el número de versión de la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulte [Registro de páginas de opciones personalizadas](../misc/registering-custom-options-pages.md).  
  
## Vea también  
 [Crear páginas de opciones mediante ensamblados de interoperabilidad](../misc/creating-options-pages-by-using-interop-assemblies.md)   
 [Crear páginas de opciones](../extensibility/internals/creating-options-pages.md)   
 [Crear páginas de opciones mediante automatización](../misc/creating-options-pages-by-using-automation.md)   
 [Controlar la configuración de opciones](../Topic/Controlling%20Options%20Settings.md)   
 [Registro de páginas de opciones personalizadas](../misc/registering-custom-options-pages.md)   
 [Abrir una página de opciones](../misc/opening-an-options-page.md)   
 [Opciones y configuración de usuario de extensión](../extensibility/extending-user-settings-and-options.md)