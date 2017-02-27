---
title: "Compatibilidad con la configuraci&#243;n de usuario | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Puntos de configuración personalizada"
  - "configuración de usuario [Visual Studio SDK], compatibilidad con la persistencia de registro"
  - "persistencia, el registro de configuración"
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Compatibilidad con la configuraci&#243;n de usuario
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un VSPackage puede definir una o más categorías de configuración, que son grupos de variables de estado que se conservan cuando un usuario elige el **Importar y exportar configuraciones** comando el **herramientas** menú. Para permitir esta persistencia, puede usar la API de configuración en el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 Una entrada del registro que se conoce como un punto de configuración personalizado y un GUID define la categoría de configuración de un VSPackage. Un VSPackage puede admitir varias categorías de configuración, cada uno define un punto de configuración personalizado.  
  
-   Las implementaciones de configuración que se basa en los ensamblados de interoperabilidad \(mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interfaz\) debe crear un punto de configuración personalizado mediante la modificación del registro o mediante un script de registro \(.rgs archivo\). Para obtener más información, consulta [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts).  
  
-   El código que usa el marco de paquete administrados \(MPF\) debe crear puntos de configuración personalizado adjuntando un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> para el VSPackage para cada punto de configuración personalizada.  
  
     Si un paquete VSPackage solo es compatible con varios puntos de configuración personalizada, cada punto de la configuración personalizada se implementa mediante una clase distinta y cada uno está registrado mediante una instancia única de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> clase. Por consiguiente, una configuración de implementación de clase puede admitir más de una categoría de configuración.  
  
## Detalles de la entrada de configuración personalizada del registro de punto  
 Se crean puntos de configuración personalizada en una entrada del registro en la siguiente ubicación: HKLM\\Software\\Microsoft\\VisualStudio\\*\< versión \>*\\UserSettings\\`<CSPName>`, donde `<CSPName>` es el nombre del punto de configuración personalizada admite el VSPackage y *\< versión \>* es la versión de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], por ejemplo 8.0.  
  
> [!NOTE]
>  La ruta de acceso raíz de HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\< versión \>* puede ser invalidado con una alternativa raíz cuando el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se inicializa el entorno de desarrollo integrado \(IDE\). Para obtener más información, consulta [Modificadores de línea de comandos](../../extensibility/command-line-switches-visual-studio-sdk.md).  
  
 A continuación se muestra la estructura de la entrada del registro:  
  
 HKLM\\Software\\Microsoft\\VisualStudio\\*\< versión \>*\\UserSettings\\  
  
 `<CSPName`\> \= s '\#12345'  
  
 Paquete \= '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'  
  
 Categoría \= '{aaaa AAAAAA aaaa aaaa YYYYYYYYY}'  
  
 ResourcePackage \= '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'  
  
 AlternateParent \= CategoryName  
  
|Nombre|Tipo|Datos|Descripción|  
|------------|----------|-----------|-----------------|  
|\(Predeterminado\)|REG\_SZ|Nombre del punto de configuración personalizada|Nombre de la clave, `<CSPName`\>, es el nombre no traducido del punto de configuración personalizada.<br /><br /> Para implementaciones basadas en MPF, nombre de la clave se obtiene combinando el `categoryName` y `objectName` argumentos de la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> constructor en `categoryName_objectName`.<br /><br /> La clave puede estar vacía o puede contener el identificador de referencia a la cadena localizada en un archivo DLL satélite. Este valor se obtiene de la `objectNameResourceID` el argumento para el <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> constructor.|  
|Paquete|REG\_SZ|GUID|El GUID del VSPackage que implementa el punto de configuración personalizada.<br /><br /> Implementaciones en función de MPF utilizando la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> de clases, use el constructor `objectType` argumento que contiene el VSPackage <xref:System.Type> y la reflexión para obtener este valor.|  
|Categoría|REG\_SZ|GUID|GUID que identifica la categoría de configuración.<br /><br /> Para implementaciones basadas en ensamblados de interoperabilidad, este valor puede ser elegidos arbitrariamente un GUID, que la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE pasa a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> y la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> métodos. Todas las implementaciones de estos dos métodos deben comprobar sus argumentos GUID.<br /><br /> Para implementaciones basadas en MPF, este GUID se obtiene mediante el <xref:System.Type> de la clase que implementa el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el mecanismo de configuración.|  
|ResourcePackage|REG\_SZ|GUID|Opcional.<br /><br /> Satélite DLL que contiene la ruta de acceso cadenas traducidas si la implementación de VSPackage no los proporciona.<br /><br /> MPF utiliza la reflexión para obtener el recurso correcto VSPackage, por lo que la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> clase no establece este argumento.|  
|AlternateParent|REG\_SZ|Nombre de la carpeta en la página de opciones de herramientas que contiene este punto de configuración personalizado.|Opcional.<br /><br /> Debe establecer este valor sólo si admite una implementación de la configuración **Opciones de herramientas** páginas que usan el mecanismo de persistencia en el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] en lugar del mecanismo en el modelo de automatización para guardar el estado.<br /><br /> En estos casos, el valor de la clave AlternateParent es la `topic` sección de la `topic.sub-topic` cadena utilizada para identificar el particular **herramientasopciones** página. Por ejemplo, para la **herramientasopciones** página `"TextEditor.Basic"` sería el valor de AlternateParent `"TextEditor"`.<br /><br /> Cuando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> genera el punto de configuración personalizado, es el mismo que el nombre de categoría.|