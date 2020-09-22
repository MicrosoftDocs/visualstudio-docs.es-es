---
title: Agregar elementos a los cuadros de diálogo Agregar nuevo elemento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecdacfc4ac65e0dc18512bfb56eb870545c66a9b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842523"
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>Adición de elementos a los cuadros de diálogo Agregar nuevo elemento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El proceso para agregar elementos al cuadro de diálogo **Agregar nuevo elemento** comienza con las claves del registro. Como se muestra en las siguientes entradas del registro, la sección AddItemTemplates contiene la ruta de acceso y el nombre del directorio en el que se colocan los elementos disponibles en el cuadro de diálogo **Agregar nuevo elemento** .  
  
> [!NOTE]
> La tabla que sigue inmediatamente al segmento de código contiene información adicional sobre la entrada del registro.  
  
 Esta sección se encuentra en [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects].  
  
 El primer GUID es el CLSID para los proyectos de este tipo; el segundo GUID indica el tipo de proyecto registrado para las plantillas para agregar elementos.  
  
 \\{C061DB26-5833-11D2-96F5-000000000000} \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \ 1  
  
 @ = "#6"  
  
 "TemplatesDir" = " \< ruta de instalación del SDK de Visual Studio \\ \VSIntegration \\ \SomeFolder \\ \SomePackage \\ \SomeProject \SomeProjectItems \\ "  
  
 "SortPriority" = dword: 00000064  
  
|Nombre|Tipo|Datos (del archivo. RGS)|Descripción|  
|----------|----------|-----------------------------|-----------------|  
|@ (Valor predeterminado)|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY%|IDENTIFICADOR de recurso para agregar plantillas de **elementos** .|  
|Val TemplatesDir|REG_SZ|% TEMPLATE_PATH% \ SomeProjectItems|Ruta de acceso de los elementos de proyecto mostrados en el cuadro de diálogo para el Asistente para **Agregar nuevo elemento** .|  
|Val SortPriority|REG_DWORD|100 ( [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)] )|Determina el criterio de ordenación en el nodo de árbol de los archivos que se muestran en el cuadro de diálogo **Agregar nuevo elemento** .|  
  
> [!NOTE]
> Los GUID para los tipos de proyecto de Visual C# y Visual Basic son los siguientes: [!INCLUDE[csprcs](../../includes/csprcs-md.md)] : {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] : {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 El directorio que se muestra para TemplateDirs, que es% TEMPLATE_PATH% \ SomeProjectItems, es el nodo en el lado izquierdo del árbol del cuadro de diálogo **Agregar nuevo elemento** . Los elementos adicionales del árbol se basan en el subdirectorio del directorio raíz. Los archivos disponibles para agregarse al proyecto son los elementos del panel derecho del cuadro de diálogo **Agregar nuevo elemento** .  
  
 Normalmente, esta carpeta contendrá los archivos de plantilla del proyecto, como un archivo HTML o. cpp de plantilla, y los archivos. vsz para iniciar asistentes. Para controlar cómo se muestran los elementos, también puede incluir archivos. vsdir para localizar los nombres de directorio y los iconos. La cadena traducida es el título que aparece en el cuadro de diálogo que representa este nodo en el árbol de diálogo Agregar nuevo elemento.  
  
 Sin embargo, no es necesario tener todo en un archivo. vsdir. Puede tener un archivo. vsdir para cada elemento del directorio. Para obtener más información, vea [Asistente (. Vsz) Descripción del](../../extensibility/internals/wizard-dot-vsz-file.md) directorio de archivos y [plantillas (. Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
> Los archivos. vsdir de los directorios de la plantilla son opcionales. Si solo desea colocar un elemento de proyecto en el directorio y mostrarlo en el cuadro de diálogo **Agregar nuevo elemento** , puede colocar ese archivo en el directorio de plantillas especificado en la instrucción TemplatesDir. El archivo se mostrará en el panel derecho del cuadro de diálogo **Agregar nuevo elemento** de ese proyecto. Sin embargo, si desea mostrar una leyenda traducida para el archivo o un icono, debe incluir al menos un archivo. vsdir en el directorio de plantillas.  
  
## <a name="grouping-project-items"></a>Agrupar elementos de proyecto  
 Si desea incluir grupos de plantillas en carpetas en el árbol del cuadro de diálogo **Agregar nuevo elemento** , debe tener subdirectorios en el directorio de plantillas raíz con los elementos que contienen. Cuando el cuadro de diálogo **Agregar nuevo elemento** se muestra a los usuarios, también verá las subcarpetas y podrá seleccionar los elementos del proyecto.  
  
 La prioridad de ordenación en el segmento de código determina dónde se creará este directorio de plantilla en el árbol con respecto a otros elementos del nodo de árbol. En el cuadro de diálogo **Agregar nuevo elemento** , la prioridad de ordenación es todo lo que debe incluir para que los elementos se muestren en la ubicación correcta en el cuadro de diálogo.  
  
 También puede implementar la <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> interfaz para filtrar lo que se muestra en el cuadro de diálogo **Agregar nuevo elemento** . Mediante la implementación de esta interfaz, puede configurar un directorio de plantilla en el disco que contenga, por ejemplo, 50 archivos de plantilla y de asistente. De este modo, puede tener distintos tipos de proyecto con 20 archivos que pertenecen a un tipo de proyecto, los otros 30 archivos que pertenecen a otro tipo de proyecto y todos los archivos disponibles en un tipo general de proyecto. De esta manera, en función de la plantilla de proyecto creada, puede mostrar un conjunto diferente de archivos de plantilla.  
  
 Por ejemplo, en un proyecto de Visual Basic, es posible que tenga proyectos web y proyectos de cliente. Los formularios Web Forms no son elementos útiles para agregarlos a un proyecto de cliente, y Windows Forms no son elementos útiles para agregarlos a un proyecto de servidor Web. Por lo tanto, puede crear un directorio de plantilla que contenga todos los archivos de ambos tipos de proyecto. A continuación, mediante la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> , puede ocultar los elementos que no deben mostrarse según el tipo de proyecto o la configuración del proyecto en el proyecto.  
  
## <a name="filtering-project-items"></a>Filtrar elementos de proyecto  
 `IVsFilterAddProjectItemDlg2` proporciona para filtrar elementos en el árbol (panel izquierdo) y archivos de proyecto (panel derecho) de las siguientes maneras:  
  
- Por los nombres localizados (los títulos que se muestran en el cuadro de diálogo que se encuentra en el archivo. vsdir) proporcionados por `IVsFilterAddProjectItemDlg` .  
  
- Por los nombres reales de los archivos y carpetas en disco (no localizados, sin archivo. vsdir) proporcionados por `IVsFilterAddProjectItemDlg` .  
  
- Por categoría, proporcionado por `IVsFilterAddProjectItemDlg2` .  
  
  Para filtrar por categoría, proporcione una cadena de categoría a un elemento del archivo. vsdir, como "Web Form" o "Client Item" en Visual Basic. A continuación, el código del cuadro de diálogo recupera la clasificación de la categoría del archivo. vsdir y le pasa. A continuación, puede pasar esa información a su implementación de `IVsFilterAddProjectItemDlg2` para filtrar el cuadro de diálogo **Agregar nuevo elemento** por categorías. También puede filtrar elementos para páginas web o como casos de aplicación de Win32 de cliente. Además, puede identificar [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] los elementos etiquetados como Microsoft Foundation Classes (MFC) o elementos de Active Template Library (ATL). Al identificar estos elementos, el sistema del proyecto puede definir sus propias clasificaciones para que el sistema se pueda filtrar en función de las categorías y las clasificaciones.  
  
  Si implementa esta funcionalidad de filtro, no es necesario asignar una tabla de todos los elementos que deben ocultarse. Simplemente puede clasificar elementos en tipos y colocar las clasificaciones en el archivo. vsdir o en los archivos. A continuación, puede ocultar cualquiera de los elementos que tienen una clasificación específica implementando la interfaz. De esta manera, puede hacer que los elementos del cuadro de diálogo **Agregar nuevo elemento** sean dinámicos en función del estado del proyecto.  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Registrar plantillas de proyecto y de elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [CATID para los objetos que se utilizan normalmente para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Agregar plantillas de proyecto y de elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Descripción del directorio de plantillas (. Archivos vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Archivo de asistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
