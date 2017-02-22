---
title: "Agregar elementos a la para agregar elementos nuevos cuadros de di&#225;logo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Agregar cuadro de diálogo nuevo elemento, agregar elementos"
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Agregar elementos a la para agregar elementos nuevos cuadros de di&#225;logo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El proceso para agregar elementos a la **Agregar nuevo elemento** inicia el cuadro de diálogo con las claves del registro. Como se muestra en las siguientes entradas del registro, la sección AddItemTemplates contiene la ruta de acceso y el nombre del directorio en los elementos que están disponibles en la **Agregar nuevo elemento** se colocan el cuadro de diálogo.  
  
> [!NOTE]
>  La tabla que sigue inmediatamente el segmento de código contiene información adicional acerca de la entrada del registro.  
  
 En esta sección se encuentra en \[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\14.0Exp\\Projects\].  
  
 El primer GUID es el CLSID para proyectos de este tipo; el segundo GUID indica el tipo de proyecto registrados para las plantillas de agregar elementos.  
  
 \\{C061DB26\-5833\-11D2\-96F5\-000000000000}\\AddItemTemplates\\TemplateDirs\\ {ACEF4EB2\-57CF\-11D2\-96F4\-000000000000} \\1  
  
 @\="\#6"  
  
 "TemplatesDir"\="\< path\\\\VSIntegration\\\\SomeFolder\\\\SomePackage\\\\SomeProject\\\\SomeProjectItems de instalación del SDK de Visual Studio"  
  
 "SortPriority" \= dword:00000064  
  
|Nombre|Tipo|Datos \(de archivo .rgs\)|Descripción|  
|------------|----------|-------------------------------|-----------------|  
|@ \(Valor predeterminado\)|REG\_SZ|\#% IDS\_ADDITEM\_TEMPLATES\_ENTRY %|Id. de recurso para **Agregar elemento** plantillas.|  
|Val TemplatesDir|REG\_SZ|%TEMPLATE\_PATH%\\ SomeProjectItems|Ruta de acceso de los elementos de proyecto en el cuadro de diálogo para el **Agregar nuevo elemento** asistente.|  
|Val SortPriority|REG\_DWORD|100 \([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]\)|Determina el criterio de ordenación en el nodo de árbol de archivos que se muestran en el **Agregar nuevo elemento** cuadro de diálogo.|  
  
> [!NOTE]
>  Los GUID para los tipos de proyecto de Visual C\# y Visual Basic son los siguientes:[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0\-301F\-11D3\-BF4B\-00C04F79EFBC}[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F\-C81C\-45F6\-A57F\-5ABD9991F28F}  
  
 El directorio indicado para TemplateDirs, que es % TEMPLATE\_PATH%\\SomeProjectItems, es el nodo en el lado izquierdo de la **Agregar nuevo elemento** árbol del cuadro de diálogo. Elementos adicionales en el árbol se basan en el subdirectorio dentro del directorio raíz. Los archivos que se agrega al proyecto son los elementos en el panel derecho de la **Agregar nuevo elemento** cuadro de diálogo.  
  
 Normalmente, esta carpeta contiene los archivos de plantilla para su proyecto como una plantilla HTML o archivo .cpp y los archivos .vsz para iniciar asistentes. Para controlar cómo se muestran los elementos, también puede incluir los archivos .vsdir para la localización de iconos y nombres de directorio. La cadena localizada es el título que aparece en el cuadro de diálogo que representa este nodo en el árbol del cuadro de diálogo Agregar nuevo elemento.  
  
 Sin embargo, no es necesario que todo esté en un archivo vsdir. Puede tener un archivo .vsdir para todos los elementos en el directorio. Para obtener más información, consulte [Asistente \(. Archivo vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md) y [Descripción del directorio de plantilla \(. Archivos VSDir\)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
>  Los archivos .vsdir en los directorios de plantillas son opcionales. Si desea colocar un elemento de proyecto en el directorio y mostrarlo en el **Agregar nuevo elemento** cuadro de diálogo, puede colocar ese archivo en el directorio de plantillas especificado en la instrucción TemplatesDir. El archivo se mostrará en el panel derecho de la **Agregar nuevo elemento** cuadro de diálogo para el proyecto. Sin embargo, si desea mostrar un título para el archivo o en un icono localizado, debe incluir al menos un archivo en el directorio de plantillas.  
  
## Agrupar elementos de proyecto  
 Si desea que contenga grupos de plantillas en carpetas en el **Agregar nuevo elemento** árbol del cuadro de diálogo, debe tener los subdirectorios bajo el directorio raíz de la plantilla con los elementos en ellos. Cuando el **Agregar nuevo elemento** cuadro de diálogo se muestra a los usuarios, también vea las subcarpetas y poder seleccionar los elementos de proyecto de ellos.  
  
 La prioridad de ordenación en el segmento de código determina dónde se creará este directorio de plantilla en el árbol con respecto a otros elementos del nodo de árbol. Para el **Agregar nuevo elemento** cuadro de diálogo, la prioridad de ordenación es todo lo que debe incluir por lo que los elementos se mostrarán en la ubicación correcta en el cuadro de diálogo.  
  
 También puede implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaz para filtrar lo que se muestra en el **Agregar nuevo elemento** cuadro de diálogo. Al implementar esta interfaz, puede configurar los directorios de una plantilla en el disco que contiene, por ejemplo, 50 archivos de plantilla y el asistente. De esa manera, puede tener diferentes tipos de proyectos con 20 archivos que pertenecen a un tipo, otros 30 archivos que pertenecen a otro tipo de proyecto y todos los archivos disponibles en un tipo de proyecto general. De esta manera, dependiendo de qué proyecto se crea la plantilla, puede mostrar un conjunto diferente de archivos de plantilla.  
  
 Por ejemplo, en un proyecto de Visual Basic, tendrá proyectos Web y proyectos de cliente. Formularios Web forms no son elementos útiles para agregar a un proyecto de cliente y formularios windows forms no son elementos útiles para agregar a un proyecto de servidor Web. Por lo tanto, puede crear un directorio de la plantilla que contiene todos los archivos para ambos tipos de proyecto. A continuación, mediante la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, puede ocultar los elementos que no deben mostrarse según el tipo de proyecto o la configuración del proyecto en el proyecto.  
  
## Filtrado de los elementos de proyecto  
 `IVsFilterAddProjectItemDlg2` se proporciona para el filtrado de elementos en el árbol \(panel izquierdo\) y archivos de proyecto \(panel derecho\) de las maneras siguientes:  
  
-   Los nombres localizados \(títulos que se muestran en el cuadro de diálogo que se encuentra en el archivo .vsdir\) proporcionada por `IVsFilterAddProjectItemDlg`.  
  
-   Por los nombres reales de los archivos y carpetas en el disco \(no traducido: ningún archivo .vsdir\) proporcionada por `IVsFilterAddProjectItemDlg`.  
  
-   Por categoría, proporcionada por `IVsFilterAddProjectItemDlg2`.  
  
 Para filtrar por categoría, especifique una cadena de categoría para un artículo en el archivo VSDir, como "Web form" o "cliente" en Visual Basic. El código del cuadro de diálogo, a continuación, recupera la clasificación de la categoría del archivo .vsdir y lo pasa a usted. A continuación, puede pasar esa información a la implementación de `IVsFilterAddProjectItemDlg2` para filtrar el **Agregar nuevo elemento** cuadro de diálogo categorías. También puede filtrar los elementos para las páginas Web o como casos de aplicación de Win32 de cliente. Además, puede identificar [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] elementos etiquetados como Microsoft Foundation Classes \(MFC\) o elementos de plantilla activa library \(ATL\). Al identificar estos elementos, el sistema del proyecto puede definir sus propias clasificaciones para que el sistema se puede filtrar según categorías y clasificaciones.  
  
 Si implementa esta funcionalidad de filtro, no es necesario asignar una tabla de todos los elementos que deberían estar ocultas. Puede clasificar elementos en tipos y colocar las clasificaciones en el archivo o archivos. A continuación, puede ocultar cualquiera de los elementos que tengan una clasificación específica mediante la implementación de la interfaz. De esta forma, puede que los elementos en el **Agregar nuevo elemento** dinámica del cuadro de diálogo se basa en el estado dentro del proyecto.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Registro de proyecto y plantillas de elementos](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATID para los objetos que se utilizan normalmente para extender proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Descripción del directorio de plantilla \(. Archivos VSDir\)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Asistente \(. Archivo vsz\)](../../extensibility/internals/wizard-dot-vsz-file.md)