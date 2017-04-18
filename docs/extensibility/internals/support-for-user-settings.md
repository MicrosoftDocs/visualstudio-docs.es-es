---
title: "Compatibilidad con la configuración de usuario | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 24bd28ad78f1cd3a21167215ed8348dc79edce6b
ms.lasthandoff: 04/05/2017

---
# <a name="support-for-user-settings"></a>Compatibilidad con la configuración de usuario
Un VSPackage puede definir una o varias categorías de configuración, que son grupos de variables de estado que se conservan cuando un usuario elige el **configuración de importación y exportación de** comando el **herramientas** menú. Para habilitar esta persistencia, se usa las API de configuración en el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 Una entrada del registro que se conoce como un punto de configuración personalizado y un GUID define la categoría de configuración de un paquete VSPackage. Un VSPackage puede admitir varias categorías de configuración, cada uno de ellos definidos por un punto de configuración personalizado.  
  
-   Las implementaciones de configuración que se basa en los ensamblados de interoperabilidad (mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>interfaz) debe crear un punto de configuración personalizado modificando el registro o mediante un script de registrador (archivo .rgs).</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> Para obtener más información, consulte [crear Scripts del registrador](/cpp/atl/creating-registrar-scripts).  
  
-   Código que utiliza Managed Package Framework (MPF) debe crear puntos de configuración personalizada adjuntando un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>para el VSPackage para cada punto de configuración personalizado.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>  
  
     Si un paquete VSPackage solo es compatible con varios puntos de configuración personalizada, cada punto de configuración personalizada se implementa mediante una clase independiente, y cada uno está registrado por una única instancia de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>clase.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> Por consiguiente, una configuración de implementación de clase puede admitir más de una categoría de configuración.  
  
## <a name="custom-settings-point-registry-entry-details"></a>Detalles de la entrada de configuración personalizada del registro de punto  
 Se crean puntos de configuración personalizada en una entrada del registro en la siguiente ubicación: HKLM\Software\Microsoft\VisualStudio\\*\<versión >*\UserSettings\\`<CSPName>`, donde `<CSPName>` es el nombre del punto de configuración personalizada de admite el VSPackage y *\<versión >* es la versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], por ejemplo 8.0.  
  
> [!NOTE]
>  La ruta de acceso raíz de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versión >* puede ser invalidado con una alternativa raíz cuando el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se inicializa el entorno de desarrollo integrado (IDE). Para obtener más información, consulte [modificadores de línea de comandos](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 La estructura de la entrada del registro se muestra a continuación:  
  
 HKLM\Software\Microsoft\VisualStudio\\*\<versión >*\UserSettings\  
  
 `<CSPName`> = '#12345' s  
  
 Paquete = '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 Categoría = '{aaaa AAAAAA aaaa aaaa YYYYYYYYY}'  
  
 ResourcePackage = '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'  
  
 AlternateParent = CategoryName  
  
|Name|Tipo|Datos|Descripción|  
|----------|----------|----------|-----------------|  
|(Predeterminado)|REG_SZ|Nombre del punto de configuración personalizada|Nombre de la clave, `<CSPName`>, es el nombre no traducido del punto de configuración personalizada.<br /><br /> Para las implementaciones en función de MPF, nombre de la clave se obtiene mediante la combinación del `categoryName` y `objectName` argumentos de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>constructor en `categoryName_objectName`.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute><br /><br /> La clave puede estar vacía o puede contener el identificador de referencia con la cadena localizada en un archivo DLL satélite. Este valor se obtiene de la `objectNameResourceID` argumento pasado a la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>constructor.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|  
|Paquete|REG_SZ|GUID|El GUID del VSPackage que implemente el punto de configuración personalizado.<br /><br /> Las implementaciones en función de MPF usando la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>de clases, utilice el constructor `objectType` argumento que contiene el VSPackage <xref:System.Type>y reflexión para obtener este valor.</xref:System.Type> </xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|  
|Categoría|REG_SZ|GUID|GUID que identifica la categoría de configuración.<br /><br /> Para las implementaciones en función de los ensamblados de interoperabilidad, este valor puede ser elegidos arbitrariamente un GUID, que el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE pasa a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A>y la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>métodos.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> Todas las implementaciones de estos dos métodos deben comprobar sus argumentos GUID.<br /><br /> Para las implementaciones en función de MPF, este GUID se obtiene mediante la <xref:System.Type>de la clase que implementa el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mecanismo de configuración.</xref:System.Type>|  
|ResourcePackage|REG_SZ|GUID|Opcional.<br /><br /> Ruta de acceso al satélite DLL que contiene cadenas traducidas si la implementación de VSPackage no los proporciona.<br /><br /> MPF utiliza la reflexión para obtener el recurso correcto VSPackage, por lo que la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>clase no establece este argumento.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|  
|AlternateParent|REG_SZ|Nombre de la carpeta en la página de opciones de herramientas que contiene este punto de configuración personalizado.|Opcional.<br /><br /> Debe establecer este valor solo si admite una implementación de las opciones **opciones de herramientas** las páginas que usan el mecanismo de persistencia en el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] en lugar del mecanismo en el modelo de automatización para guardar el estado.<br /><br /> En estos casos, es el valor de la clave AlternateParent el `topic` sección de la `topic.sub-topic` cadena utilizada para identificar el determinado **ToolsOptions** página. Por ejemplo, para la **ToolsOptions** página `"TextEditor.Basic"` sería el valor de AlternateParent `"TextEditor"`.<br /><br /> Cuando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>genera el punto de configuración personalizado, es el mismo que el nombre de categoría.</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>|
