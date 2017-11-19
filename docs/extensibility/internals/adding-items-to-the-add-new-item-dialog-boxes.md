---
title: "Agregar elementos a la para agregar elementos nuevos cuadros de diálogo | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a16698863e92e5bbae4e888502788dd76b04f56
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>Agregar elementos a la para agregar elementos nuevos cuadros de diálogo
El proceso para agregar elementos a la **Agregar nuevo elemento** inicia el cuadro de diálogo con las claves del registro. Como se muestra en las siguientes entradas del registro, la sección AddItemTemplates contiene la ruta de acceso y el nombre del directorio de los elementos que están disponibles en la **Agregar nuevo elemento** se colocan el cuadro de diálogo.  
  
> [!NOTE]
>  La tabla que sigue inmediatamente el segmento de código contiene información adicional sobre la entrada del registro.  
  
 En esta sección se encuentra en [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects].  
  
 El primer GUID es el CLSID para los proyectos de este tipo; el segundo GUID indica el tipo de proyecto registrados para las plantillas de agregar elementos.  
  
 \\{C061DB26-5833-11D2-96F5-000000000000} \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \1  
  
 @="#6"  
  
 "TemplatesDir"="\<ruta de instalación del SDK de Visual Studio\\\VSIntegration\\\SomeFolder\\\SomePackage\\\SomeProject\\\SomeProjectItems"  
  
 "SortPriority" = dword:00000064  
  
|Name|Tipo|Datos (desde el archivo .rgs)|Descripción|  
|----------|----------|-----------------------------|-----------------|  
|@ (Valor predeterminado)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY %|Id. de recurso para **Agregar elemento** plantillas.|  
|Val TemplatesDir|REG_SZ|%TEMPLATE_PATH%\ SomeProjectItems|Ruta de acceso de los elementos de proyecto que se muestra en el cuadro de diálogo para la **Agregar nuevo elemento** asistente.|  
|Val SortPriority|REG_DWORD|100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)])|Determina el criterio de ordenación en el nodo de árbol de archivos que se muestran en la **Agregar nuevo elemento** cuadro de diálogo.|  
  
> [!NOTE]
>  Los GUID para los tipos de proyectos de Visual C# y Visual Basic son los siguientes:[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 El directorio indicado para TemplateDirs, que es % TEMPLATE_PATH%\SomeProjectItems, es el nodo en el lado izquierdo de la **Agregar nuevo elemento** árbol del cuadro de diálogo. Elementos adicionales en el árbol se basan en el subdirectorio dentro del directorio raíz. Los archivos disponibles para agregarlos al proyecto son los elementos en el panel derecho de la **Agregar nuevo elemento** cuadro de diálogo.  
  
 Normalmente, esta carpeta contendrá los archivos de plantilla para el proyecto como una plantilla de HTML o archivo .cpp y cualquier archivo .vsz para iniciar asistentes. Para controlar cómo se muestran los elementos, también puede incluir los archivos .vsdir para localizar los iconos y nombres de directorio. La cadena adaptada es el título que aparece en el cuadro de diálogo que representa este nodo en el árbol de cuadro de diálogo Agregar nuevo elemento.  
  
 Sin embargo, no es necesario tener todo en un archivo. Puede tener un archivo .vsdir para todos los elementos en el directorio. Para obtener más información, vea [asistente (. Archivo vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) y [descripción del directorio de plantilla (. Archivos VSDir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
>  Los archivos .vsdir en los directorios de plantilla son opcionales. Si desea colocar un elemento de proyecto en el directorio y mostrarlo en el **Agregar nuevo elemento** cuadro de diálogo, puede colocar ese archivo en el directorio de plantillas especificado en la instrucción TemplatesDir. El archivo, a continuación, se mostrará en el panel derecho de la **Agregar nuevo elemento** cuadro de diálogo para ese proyecto. Sin embargo, si desea mostrar un título localizado para el archivo o en un icono, debe incluir al menos un archivo en el directorio de plantillas.  
  
## <a name="grouping-project-items"></a>Elementos de proyecto de agrupación  
 Si desea que contenga grupos de plantillas en las carpetas en el **Agregar nuevo elemento** árbol del cuadro de diálogo, debe tener subdirectorios bajo el directorio raíz de la plantilla con los elementos contenidos en ellas. Cuando el **Agregar nuevo elemento** aparece el cuadro de diálogo a los usuarios, también vea las subcarpetas y poder seleccionar elementos de proyecto de ellos.  
  
 La prioridad de ordenación en el segmento de código determina donde se creará este directorio de plantilla en el árbol con respecto a otros elementos del nodo de árbol. Para el **Agregar nuevo elemento** cuadro de diálogo, la prioridad de ordenación es todo lo que debe incluir por lo que los elementos se mostrarán en la ubicación correcta en el cuadro de diálogo.  
  
 También puede implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaz para filtrar lo que se muestra en el **Agregar nuevo elemento** cuadro de diálogo. Al implementar esta interfaz, puede configurar los directorios de una plantilla en el disco que contenga, por ejemplo, 50 archivos de plantilla y el asistente. De esa manera, puede tener diferentes tipos de proyectos con 20 archivos que pertenecen al tipo de un proyecto, los otros 30 archivos que pertenecen a otro tipo de proyecto y todos los archivos disponibles en un tipo general del proyecto. De esta manera, dependiendo de qué proyecto se crea la plantilla, puede mostrar un conjunto diferente de archivos de plantilla.  
  
 Por ejemplo, en un proyecto de Visual Basic, podría tener proyectos Web y proyectos de cliente. Formularios Web forms no son elementos útiles para agregar a un proyecto de cliente y formularios windows forms no son elementos útiles para agregar a un proyecto de servidor Web. Por lo tanto, puede crear un directorio de plantilla que contiene todos los archivos para ambos tipos de proyecto. A continuación, mediante la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, puede ocultar los elementos que no deben mostrarse según el tipo de proyecto o la configuración del proyecto en el proyecto.  
  
## <a name="filtering-project-items"></a>Filtrado de los elementos de proyecto  
 `IVsFilterAddProjectItemDlg2`se proporciona para el filtrado de elementos en el árbol (panel izquierdo) y archivos de proyecto (panel derecho) de las maneras siguientes:  
  
-   Los nombres localizados (títulos que se muestran en el cuadro de diálogo que se encuentra en el archivo.) proporcionada por `IVsFilterAddProjectItemDlg`.  
  
-   Por los nombres reales de los archivos y carpetas en el disco (no localizada, ningún archivo) proporcionada por `IVsFilterAddProjectItemDlg`.  
  
-   Por categoría, proporcionada por `IVsFilterAddProjectItemDlg2`.  
  
 Para filtrar por categoría, especifique una cadena de categoría para un artículo en el archivo .vsdir, por ejemplo, "Web form" o "cliente" en Visual Basic. El código del cuadro de diálogo, a continuación, recupera la clasificación de categoría desde el archivo y pasa a usted. A continuación, puede pasar esa información a su implementación de `IVsFilterAddProjectItemDlg2` para filtrar el **Agregar nuevo elemento** categorías de cuadro de diálogo. También puede filtrar los elementos para las páginas Web o como casos de aplicación de Win32 de cliente. Además, puede identificar [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] elementos etiquetados como Microsoft Foundation Classes (MFC) o elementos de (ATL) de la biblioteca de plantillas activas. Al identificar estos elementos, el sistema del proyecto puede definir sus propias clasificaciones para que el sistema se puede filtrar según categorías y clasificaciones.  
  
 Si implementa esta funcionalidad de filtro, no es necesario asignar una tabla de todos los elementos que deberían estar ocultas. Simplemente puede clasificar elementos en tipos y colocar las clasificaciones en el archivo o los archivos. A continuación, puede ocultar cualquiera de los elementos que tienen una clasificación específica mediante la implementación de la interfaz. En este modo, puede hacer que los elementos de la **Agregar nuevo elemento** dinámicos del cuadro de diálogo en función del estado en el proyecto.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Registro de proyecto y plantillas de elementos](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATID para los objetos que se usan normalmente para extender proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Descripción de directorio de la plantilla (. Archivos VSDir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Archivos de asistentes (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)