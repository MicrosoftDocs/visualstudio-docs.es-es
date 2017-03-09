---
title: "Registro de p&#225;ginas de opciones personalizadas | Microsoft Docs"
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
  - "registro, páginas de opciones de herramientas personalizadas"
  - "Páginas de opciones de herramientas [Visual Studio SDK], registro"
ms.assetid: 0ac6377d-a679-4f7d-be80-451c829b56f2
caps.latest.revision: 28
caps.handback.revision: 28
manager: "douge"
---
# Registro de p&#225;ginas de opciones personalizadas
Para que una página de **Opciones de herramientas** esté disponible para los usuarios y a la automatización de, debe registrarse correctamente con el entorno de desarrollo integrado de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(IDE\).  
  
 Las páginas de**Opciones de herramientas** basadas en el managed package se registran aplicando una instancia de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> el Paquete que proporciona a la página.  Compatibilidad con la automatización se indica estableciendo la propiedad de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> a `true`.  
  
## Registro de la página opciones de herramientas  
 La integración de una página personalizada de **Opciones de herramientas** con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] requiere la creación de una entrada de Registro en la ubicación siguiente: HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<versión\>*\\ ToolsOptionsPages, donde es la versión *\<versión\>* de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], por ejemplo 8,0.  
  
 La entrada tiene una clave principal a la categoría \(`<PageCategory>`\) de la página de **Opciones de herramientas** , y una subclave que contiene el nombre de la subcategoría de la página \(`<PageSubCategory>`\).  
  
 Por ejemplo, la página de **Opciones de herramientas** identificada en la cadena, **TextEditor.Basic**, tiene un \=textEditor de `<PageCategory>`de la clave del Registro con una subclave de `<PageSubCategory>`\=Basic.  
  
 La estructura de la entrada de Registro se siguiente:  
  
 HKLM \\ software \\ Microsoft \\ VisualStudio \\*\<versión\>*\\ ToolsOptionsPages \\  
  
 `<PageCategory>` \= '\#12345'  
  
 Paquete \= “{}”  
  
 ResourcePackage \= “{YYYYYY AAAA AAAA AAAA YYYYYYYYY}”  
  
 HKLM \\ software \\ Microsoft \\ VisualStudio \\*\<versión\>*\\ ToolsOptionsPages \\`<PageCategory>`  
  
 `<PageSubCategory>>` \= '\#67890'  
  
 Página \= “{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}”  
  
 Paquete \= “{AAAAAA AAAA AAAA AAAA AAAAAAAAA}”  
  
 ResourcePackage \= “{BBBBBB BBBB BBBB BBBB BBBBBBBBB}”  
  
 NoShowAllView \= 0\/1  
  
 La tabla siguiente se enumeran los valores bajo HKLM \\ el software \\ Microsoft \\ VisualStudio \\*\<versión\>*\\ ToolsOptionsPages \\`<PageCategory>`.  
  
|Name|Tipo|Datos|Descripción|  
|----------|----------|-----------|-----------------|  
|\(Valor predeterminado\)|REG\_SZ|El nombre de categoría canónico de la página personalizada de **Opciones de herramientas**|El nombre de clave, `<PageCategory>`, es el nombre de categoría no traducido canónico de la página de **Opciones de herramientas** . **Note:**  Si se admite la automatización, los nombres no\-localizados canónicos de la categoría y la subcategoría se utilizan para obtener la colección de <xref:EnvDTE.Properties> de una página de **Opciones de herramientas** .  Para obtener más información, vea [Usar páginas de opciones](../misc/using-options-pages.md). <br /><br /> Para las implementaciones basadas en el managed package, el \> de `<PageCategory`se obtiene del argumento de `categoryName` al constructor de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .<br /><br /> La clave puede estar vacía, o puede contener el identificador de referencia a la cadena traducida en un archivo DLL satélite de una implementación.<br /><br /> Para las implementaciones basadas en el managed package, este valor se obtiene del argumento de `categoryResourceID` al constructor de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .|  
|Paquete|REG\_SZ|GUID|GUID del Paquete que implementa la página personalizada de **Opciones de herramientas** .<br /><br /> Implementaciones basadas en el managed package mediante la reflexión de uso de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> para obtener este valor.|  
|ResourcePackage|REG\_SZ|GUID|Opcional.<br /><br /> Un archivo DLL satélite que contiene las cadenas localizadas si el Paquete que implementa no las proporciona.<br /><br /> El managed package utiliza la reflexión para obtener el paquete correcto de recursos, por lo que <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> no establece este argumento.|  
  
 La tabla siguiente se enumeran los valores bajo HKLM \\ el software \\ Microsoft \\ VisualStudio \\*\<versión\>*\\ ToolsOptionsPages \\`<PageCategory>`\\`<PageSubCategory>`.  
  
|Name|Tipo|Datos|Descripción|  
|----------|----------|-----------|-----------------|  
|\(Valor predeterminado\)|REG\_SZ|El nombre canónico de subcategoría de la página personalizada de **Opciones de herramientas**|El nombre de clave, \> de `<PageSubCategory`, es el nombre no traducido canónico de subcategoría de la página de **Opciones de herramientas** . **Note:**  Si se admite la automatización, los nombres no\-localizados canónicos de la categoría y la subcategoría se utilizan para obtener la colección de <xref:EnvDTE.Properties> de una página de **Opciones de herramientas** .  Para obtener más información, vea [Usar páginas de opciones](../misc/using-options-pages.md). <br /><br /> Para las implementaciones basadas en el managed package, el \> de `<PageSubegory`se obtiene del argumento de `pageName` al constructor de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .<br /><br /> La clave puede estar vacía, o puede contener el identificador de referencia a la cadena traducida en un archivo DLL satélite de una implementación.<br /><br /> Para las implementaciones basadas en el managed package, este valor se obtiene del argumento de `pageNameResourceID` al constructor de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .|  
|Page|REG\_SZ|GUID|GUID del objeto que implementa la página personalizada de **Opciones de herramientas** .<br /><br /> Las implementaciones basadas en el managed package mediante <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> utilizan el argumento de `pageType` de constructor que contiene <xref:System.Type> y reflexión de VSPackage para obtener este valor.|  
|Paquete|REG\_SZ|GUID|Implementaciones basadas en el managed package mediante la reflexión de uso de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> para obtener este valor.|  
|ResourcePackage|REG\_SZ|GUID|Opcional.<br /><br /> Un archivo DLL satélite que contiene las cadenas localizadas si el Paquete que implementa no las proporciona.<br /><br /> El managed package utiliza la reflexión para obtener el archivo DLL de recursos correcta, por lo que <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> no establece este argumento.|  
|NoShowAllView|REG\_DWORD|0 ó 1|Opcional.<br /><br /> Indica si una página determinada de **Opciones de herramientas** debe aparecer en la vista \(predeterminada\) compleja de las páginas de **Opciones de herramientas** .  Admite los entornos de programación, como Visual Basic, que tienen páginas especiales de **Opciones de herramientas** para agregar valores comunes para proporcionar a los usuarios vistas simplificadas especializadas de opciones.<br /><br /> Si la entrada de REG\_DWORD es cero, la página de **Opciones de herramientas** no aparece en una vista compleja.<br /><br /> Para obtener más información, vea [Opciones \(Cuadro de diálogo\)](../ide/reference/options-dialog-box-visual-studio.md).<br /><br /> Las implementaciones basadas en el managed package pueden establecer este valor estableciendo la propiedad de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.NoShowAllView%2A> a `true` en el constructor de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .|  
  
 Un VSPackage o un objeto basado en un único ensamblado de interoperabilidad puede implementar más de una página de **Opciones de herramientas** .  Cada implementación requiere una nueva entrada en HKLM \\ software \\ Microsoft \\ VisualStudio \\*\<versión\>*\\ ToolsOptionsPages.  
  
 Como el managed package crea instancias del objeto que proporciona a una página de **Opciones de herramientas** , cada página debe tener su propio objeto de implementación, independientemente de la implementación de un Paquete de <xref:Microsoft.VisualStudio.Shell.Package>.  
  
## Compatibilidad de automatización  
 Si la compatibilidad de automatización se utiliza para implementar una página de **Opciones de herramientas** , debe registrarse como un proveedor de automatización.  Para utilizar la automatización para la administración de la propiedad, y utilizar los mecanismos de persistencia para guardar el estado de la página de **Opciones de herramientas** , debe registrarse como un proveedor de `AutomationProperty` .  
  
### Registre un VSPackage como proveedor de automatización \(Solo para las páginas de opciones las herramientas basadas en ensamblados de Interoperabilidad\)  
 Las páginas de**Opciones de herramientas** basadas en un ensamblado de interoperabilidad se implementan como parte de las clases de implementación de un Paquete.  
  
 En este caso, si una página de **Opciones de herramientas** es admitir automatización, el paquete VSPackage basado en ensamblados interoperabilidad se debe registrar como un proveedor de automatización.  
  
> [!NOTE]
>  Compatibilidad de automatización en el managed package proporcionado por una independiente del objeto de la implementación del Paquete.  Si ese objeto admite la automatización, esto se registra mediante la propiedad de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> de constructor de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .  
  
 La entrada para registrar un VSPackage como proveedor de automatización tiene el formato HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<versión\>*\\ paquetes \\*\<PackageGUID\>*\\ automatización, donde es la versión *\<versión\>* de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(como 8,0\) y *\<PackageGUID\>* es el GUID del Paquete que implementa el objeto de automatización.  
  
> [!NOTE]
>  La ruta de acceso raíz HKEY\_LOCAL\_MACHINE \\ de SOFTWARE \\ de Microsoft \\ VisualStudio \\*\<versión\>* se puede reemplazar con la raíz alternativa cuando se inicializa el shell de Visual Studio.  Para obtener más información, vea [Modificadores de línea de comandos](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 La estructura de la entrada del Registro es:  
  
 HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<versión\>*\\ paquetes \\*\<PackageGUID\>*\\ automatización  
  
 `<AutomationObjectName>`  
  
|Name|Tipo|Datos|Descripción|  
|----------|----------|-----------|-----------------|  
|Automatización|REG\_SZ|No definido|No definido.<br /><br /> La presencia de esta clave indica que el Paquete al que hace referencia *\<PackageGUID\>* admita automatización.<br /><br /> El campo se puede utilizar para almacenar la documentación.<br /><br /> <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> crea automáticamente esta clave para las aplicaciones basadas en el managed package.|  
|`<AutomationObjectName>`|REG\_SZ|El nombre canónico de objetos de automatización proporcionado|Sólo el nombre de clave es pertinente.  Se utiliza en operaciones de automatización.<br /><br /> El campo se puede utilizar para almacenar la documentación.<br /><br /> Para las implementaciones basadas en el managed package, el nombre de esta clave está determinado por el argumento de `name` al constructor de <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> .<br /><br /> Si el constructor de <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute> tiene una cadena válida proporcionada a la propiedad de <xref:Microsoft.VisualStudio.Shell.ProvideAutomationObjectAttribute.Description%2A> , este valor se inserta aquí.|  
  
### Registre una página opciones de herramientas como admitir automatización  
 El managed package e implementaciones ensamblado\-basadas interoperabilidad de las páginas de **Opciones de herramientas** deben registrar para permitir el acceso de automatización a una página de **Opciones de herramientas** .  Esto incluye los mecanismos y acceso de persistencia de la propiedad de automatización a la página con <xref:EnvDTE>.  Es el registro de VSPackage propio como proveedor de servicios de automatización.  
  
 Como ocurre con el registro de la página de **Opciones de herramientas** mencionado anteriormente, la entrada tiene una clave principal a la categoría \(`<PageCategory>`\) de la página de **Opciones de herramientas** , y una subclave que contiene el nombre de la subcategoría de la página \(`<PageSubcategory>`\).  
  
 Si utiliza el managed package, utilice <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> de registrar una clase como proporcionar a una página de **Opciones de herramientas** y establecer la propiedad de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsAutomation%2A> a `true` para indicar que la página admite la automatización.  
  
 La entrada del Registro se encuentra en HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<versión\>*\\ AutomationProperties, donde es la versión *\<versión\>* de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], por ejemplo 8,0.  
  
> [!NOTE]
>  La ruta de acceso raíz HKEY\_LOCAL\_MACHINE \\ de SOFTWARE \\ de Microsoft \\ VisualStudio \\*\<versión\>* se puede reemplazar con la raíz alternativa cuando se inicializa el shell de Visual Studio, para obtener más información, vea [Modificadores de línea de comandos](../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 La estructura de la entrada de Registro se siguiente:  
  
 HKEY\_LOCAL\_MACHINE \\ SOFTWARE \\ Microsoft \\ VisualStudio \\*\<versión\>\\*AutomationProperties  
  
 `<PageCategory>` \= ‘\#456’  
  
 ResourcePackage \= “{}”  
  
 `<PageSubCategory>` \= ‘\#789’  
  
 Paquete \= “{YYYYYY AAAA AAAA AAAA YYYYYYYYY}”  
  
 Nombre \= “`<PageCategory>` .`<PageSubcategory>`”  
  
 “ProfileSave” \= 1\/0  
  
 La tabla siguiente muestra los valores en HKEY\_LOCAL\_MACHINE \\ el SOFTWARE \\ Microsoft \\ VisualStudio \\*\<versión\>*\\ AutomationProperties \\`<PageCategory>`.  
  
|Name|Tipo|Datos|Descripción|  
|----------|----------|-----------|-----------------|  
|\(Valor predeterminado\)|REG\_SZ|El nombre de categoría canónico de la página personalizada de **Opciones de herramientas**|El nombre de clave, \> de `<PageCategory`, es el nombre no traducido canónico de la categoría de la página de **Opciones de herramientas** . **Note:**  Si se admite la automatización, los nombres no\-localizados canónicos de la categoría y la subcategoría se utilizan para obtener la colección de <xref:EnvDTE.Properties> de una página de **Opciones de herramientas** .  Para obtener más información, vea [Usar páginas de opciones](../misc/using-options-pages.md). <br /><br /> La clave puede estar vacía, o puede contener el identificador de referencia a la cadena traducida en un archivo DLL satélite de una implementación.<br /><br /> Para las implementaciones basadas en el managed package, el \> de `<PageCategory`se obtiene del argumento de `categoryName` al constructor de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .|  
|ResourcePackage|REG\_SZ|GUID|Opcional.<br /><br /> Un archivo DLL satélite que contiene las cadenas localizadas si el Paquete que implementa no las proporciona.<br /><br /> El managed package utiliza la reflexión para obtener el recurso correcto VSPackage, por lo que <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> no establece este argumento.|  
  
 La tabla siguiente muestra los valores en HKEY\_LOCAL\_MACHINE \\ el SOFTWARE \\ Microsoft \\ VisualStudio \\*\<versión\>*\\ AutomationProperties \\`<PageCategory>\<PageSubCategory>`.  
  
|Name|Tipo|Datos|Descripción|  
|----------|----------|-----------|-----------------|  
|\(Valor predeterminado\)|REG\_SZ|El nombre de la subcategoría de la página personalizada de **Opciones de herramientas**|El nombre de clave, \> de `<PageSubCategory`, es el nombre no traducido canónico de subcategoría de la página de **Opciones de herramientas** . **Note:**  Si se admite la automatización, los nombres no\-localizados canónicos de la categoría y la subcategoría se utilizan para obtener la colección de <xref:EnvDTE.Properties> de una página de **Opciones de herramientas** .  Para obtener más información, vea [Usar páginas de opciones](../misc/using-options-pages.md). <br /><br /> La clave puede estar vacía, o puede contener el identificador de referencia a la cadena traducida en un archivo DLL satélite de una implementación.<br /><br /> Para las implementaciones basadas en el managed package, `<PageSubCategory>` se obtiene del argumento de `pageName` al constructor de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> .|  
|Paquete|REG\_SZ|GUID|GUID del Paquete que implementa la página personalizada de **Opciones de herramientas** .<br /><br /> Implementaciones basadas en el managed package mediante la reflexión de uso de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> para obtener este valor.|  
|Name|REG\_SZ|Nombre de la colección properties de página de **Opciones de herramientas**|La cadena de `<PageCategory>.<PageSubCategory>` utilizada para hacer referencia a la página de **Opciones de herramientas** .  Para obtener más información, vea [Usar páginas de opciones](../misc/using-options-pages.md).<br /><br /> Para las implementaciones basadas en el managed package, el nombre se obtiene de argumentos del constructor de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> y tiene el formato `categoryName.pageName`.|  
|ProfileSave|DWORD|1\/0|Opcional.<br /><br /> Este valor indica si la configuración de **Opciones de herramientas** son guardadas mediante el mecanismo de los valores de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cuando un usuario hace clic en el comando de **Opciones para importar o exportar** en el menú de **Herramientas** .<br /><br /> Si la clave está presente y el valor es 1, la página de **Opciones de herramientas** se soliciten la compatibilidad de configuración.<br /><br /> Las implementaciones basadas en el managed package establecen este valor si proporcionan al constructor de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> con la propiedad de <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> establecida en `true`.|  
  
## Vea también  
 [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts)   
 [Usar páginas de opciones](../misc/using-options-pages.md)   
 [Crear páginas de opciones mediante ensamblados de interoperabilidad](../misc/creating-options-pages-by-using-interop-assemblies.md)   
 [Cómo: Crear páginas de opciones personalizadas](../Topic/How%20to:%20Create%20Custom%20Options%20Pages.md)   
 [Páginas Opciones](../misc/options-pages.md)   
 [Compatibilidad de automatización para las páginas de opciones](../extensibility/internals/automation-support-for-options-pages.md)