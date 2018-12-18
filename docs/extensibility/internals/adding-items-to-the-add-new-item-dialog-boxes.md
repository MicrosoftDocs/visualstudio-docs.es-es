---
title: Agregar elementos a la Agregar nuevo elemento de los cuadros de diálogo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b98e696def519cea6d3644d0ef3a48bc82c19136
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812587"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Agregar elementos al cuadro de diálogo Agregar nuevo elemento
El proceso para agregar elementos a la **Agregar nuevo elemento** inicia el cuadro de diálogo con las claves del registro. Como se muestra en las siguientes entradas del registro, el **AddItemTemplates** sección contiene la ruta de acceso y el nombre del directorio en los elementos que ponen a disposición de los **Agregar nuevo elemento** se colocan el cuadro de diálogo.  

> [!NOTE]
>  La tabla que sigue inmediatamente el segmento de código contiene información adicional sobre la entrada del registro.  

 En esta sección se encuentra en **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects**.

 El primer GUID es el CLSID para los proyectos de este tipo; el segundo GUID indica el tipo de proyecto registrado para las plantillas de agregar elementos:  

 **\\{C061DB26-5833-11D2-96F5-000000000000} \\AddItemTemplates\\TemplatesDir\\{ACEF4EB2-57CF-11D2-96F4-000000000000}\\1**

 **@** = #6 

 **TemplatesDir** = \\&lt;ruta de instalación del SDK de Visual Studio&gt;\\VSIntegration\\&lt;SomeFolder&gt; \\ &lt;SomePackage&gt;\\&lt;SomeProject&gt;\\&lt;SomeProjectItems&gt;

 **SortPriority** = dword:00000064


| nombre | Tipo | Datos (desde *.rgs* archivo) | Descripción |
|------------------|-----------| - | - |
| @ (Valor predeterminado) | REG_SZ | #% IDS_ADDITEM_TEMPLATES_ENTRY % | Identificador de recurso para **Agregar elemento** plantillas. |
| Val TemplatesDir | REG_SZ | % TEMPLATE_PATH %\\&lt;SomeProjectItems&gt; | Ruta de acceso de los elementos de proyecto que se muestra en el cuadro de diálogo para la **Agregar nuevo elemento** asistente. |
| Val SortPriority | REG_DWORD | 100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]) | Determina el criterio de ordenación en el nodo de árbol de archivos que se muestran en el **Agregar nuevo elemento** cuadro de diálogo. |

> [!NOTE]
>  Los GUID de los tipos de proyecto de Visual Basic y Visual C# son los siguientes: 
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  

 El directorio que aparece para **TemplatesDir**, que es *TEMPLATE_PATH %\\&lt;SomeProjectItems&gt;*, es el nodo en el lado izquierdo de la **agregar Nuevo elemento** árbol del cuadro de diálogo. Elementos adicionales en el árbol se basan en el subdirectorio dentro del directorio raíz. Los archivos disponibles para agregarse al proyecto son los elementos en el panel derecho de la **Agregar nuevo elemento** cuadro de diálogo.  

 Normalmente, esta carpeta contendrá los archivos de plantilla para su proyecto como una plantilla HTML o *.cpp* archivo y cualquier *.vsz* archivos para iniciar asistentes. Para controlar cómo se muestran los elementos, también puede incluir *.vsdir* los archivos para localizar los nombres de directorio y los iconos. La cadena localizada es el título que aparece en el cuadro de diálogo que representa este nodo en el **Agregar nuevo elemento** árbol del cuadro de diálogo.  

 Sin embargo, no es necesario que tener todo en uno *.vsdir* archivo. Puede tener una *.vsdir* archivo para todos los elementos en el directorio. Para obtener más información, consulte [archivo asistentes (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) y [archivos de descripción (.vsdir) del directorio de plantilla](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  

> [!NOTE]
>  El *.vsdir* archivos en los directorios de la plantilla son opcionales. Si solo desea colocar un elemento de proyecto en el directorio y lo mostrará en el **Agregar nuevo elemento** cuadro de diálogo, puede colocar ese archivo en el directorio de plantillas especificado en el **TemplatesDir** instrucción. El archivo, a continuación, se mostrará en el panel derecho de la **Agregar nuevo elemento** cuadro de diálogo para ese proyecto. Sin embargo, si desea mostrar un título localizado para el archivo o en un icono, debe incluir al menos una *.vsdir* archivo en el directorio de plantillas.  

## <a name="group-project-items"></a>Agrupar elementos de proyecto  
 Si desea que contenga grupos de plantillas en las carpetas en el **Agregar nuevo elemento** árbol del cuadro de diálogo, debe tener los subdirectorios en el directorio raíz de la plantilla con los elementos en ellos. Cuando el **Agregar nuevo elemento** cuadro de diálogo se muestra a los usuarios, también vea las subcarpetas y poder seleccionar los elementos de proyecto de ellos.  

 La prioridad de ordenación en el segmento de código determina donde se creará este directorio de plantilla en el árbol con respecto a otros elementos del nodo de árbol. Para el **Agregar nuevo elemento** cuadro de diálogo, la prioridad de ordenación es todo lo que debe incluir por lo que los elementos se mostrarán en la ubicación correcta en el cuadro de diálogo.  

 También puede implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaz para filtrar lo que se muestra en el **Agregar nuevo elemento** cuadro de diálogo. Al implementar esta interfaz, puede configurar los directorios de una plantilla en el disco que contiene, por ejemplo, 50 archivos de plantilla y el asistente. De esa manera, puede tener diferentes tipos de proyectos con 20 archivos que pertenecen al tipo de un proyecto, los demás 30 archivos que pertenecen a otro tipo de proyecto y todos los archivos disponibles en un tipo de proyecto general. De esta manera, dependiendo de qué proyecto se crea la plantilla, puede mostrar un conjunto diferente de archivos de plantilla.  

 Por ejemplo, en un proyecto de Visual Basic, podría tener los proyectos Web y proyectos de cliente. Formularios Web forms no son elementos útiles para agregar a un proyecto de cliente y formularios windows forms no son elementos útiles para agregar a un proyecto de servidor Web. Por lo tanto, puede crear un directorio de plantilla que contiene todos los archivos para ambos tipos de proyecto. A continuación, implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, puede ocultar los elementos que no deben mostrarse según el tipo de proyecto o la configuración del proyecto en el proyecto.  

## <a name="filter-project-items"></a>Filtrar elementos de proyecto  
 `IVsFilterAddProjectItemDlg2` se proporciona para el filtrado de elementos en el árbol (panel izquierdo) y archivos de proyecto (panel derecho) de las maneras siguientes:  

- Los nombres localizados (títulos que se muestran en el cuadro de diálogo que se encuentra en la *.vsdir* archivo) proporcionado por `IVsFilterAddProjectItemDlg`.  

- Por los nombres reales de los archivos y carpetas en el disco (no localizado, no hay *.vsdir* archivo) proporcionado por `IVsFilterAddProjectItemDlg`.  

- Por categoría, proporcionada por `IVsFilterAddProjectItemDlg2`.  

  Para filtrar por categoría, proporcione una cadena de categoría a un elemento en el *.vsdir* archivo, como *formulario Web* o *elemento cliente* en Visual Basic. El código del cuadro de diálogo, a continuación, recupera la clasificación de categoría desde la *.vsdir* de archivo y lo pasa a usted. A continuación, puede pasar esa información a la implementación de `IVsFilterAddProjectItemDlg2` para filtrar el **Agregar nuevo elemento** categorías de cuadro de diálogo. También puede filtrar los elementos para las páginas Web o como casos de aplicación de Win32 de cliente. Además, puede identificar [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] elementos etiquetados como Microsoft Foundation Classes (MFC) o elementos de plantillas activo library (ATL). Al identificar estos elementos, el sistema del proyecto puede definir sus propias clasificaciones para que el sistema se puede filtrar en función de las categorías y clasificaciones.  

  Si implementa esta funcionalidad de filtro, no es necesario asignar una tabla de todos los elementos que deberían estar ocultas. Simplemente puede clasificar elementos en tipos y coloque las clasificaciones en el *.vsdir* archivo o archivos. A continuación, puede ocultar cualquiera de los elementos que tienen una clasificación específica mediante la implementación de la interfaz. En este modo, puede hacer que los elementos de la **Agregar nuevo elemento** dinámicos del cuadro de diálogo en función del estado del proyecto.  

## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Registrar las plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATID para los objetos que se suelen usar para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Agregar proyecto y plantillas de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Archivos de descripción (.vsdir) del directorio de plantilla](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Archivos de asistentes (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)