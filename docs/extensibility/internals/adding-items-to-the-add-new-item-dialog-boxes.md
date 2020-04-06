---
title: Adición de elementos a los cuadros de diálogo Agregar nuevo elemento ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7f9e5c792785a23ad1674a50abeb4eb6d3cba9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710213"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Agregar elementos al cuadro de diálogo Agregar nuevo elemento
El proceso para agregar elementos al cuadro de diálogo **Agregar nuevo elemento** comienza con las claves del Registro. Como se muestra en las siguientes entradas del Registro, la sección **AddItemTemplates** contiene la ruta de acceso y el nombre del directorio en el que se colocan los elementos disponibles en el cuadro de diálogo **Agregar nuevo elemento.**

> [!NOTE]
> La tabla inmediatamente después del segmento de código contiene información adicional sobre la entrada del Registro.

 Esta sección se encuentra en **HKEY_LOCAL_MACHINE, SOFTWARE, Microsoft, VisualStudio, 14,0Exp, Proyectos**.

 El primer GUID es el CLSID para proyectos de este tipo; el segundo GUID indica el tipo de proyecto registrado para las plantillas Agregar elementos:

 **\\C061DB26-5833-11D2-96F5-0000000000000000 \\AddItemTemplates\\TemplatesDir\\áACEF4EB2-57CF-11D2-96F4-0000000000000 1\\**

 **@**• #6

 **TemplatesDir** = \\&gt;\\&lt;\\&lt;&gt;\\&lt;&gt;\\&lt;Visual Studio&gt;\\SDK ruta de instalación VSIntegration SomeFolder SomeProject SomeProject Items&lt;&gt;

 **SortPriority** á dword:00000064

| Nombre | Tipo | Datos (desde el archivo *.rgs)* | Descripción |
|------------------|-----------| - | - |
| (Predeterminado) | REG_SZ | %IDS_ADDITEM_TEMPLATES_ENTRY% | Identificador de recurso para agregar plantillas **de elemento.** |
| Val TemplatesDir | REG_SZ | %TEMPLATE_PATH%\\&lt;SomeProjectItems&gt; | Ruta de acceso de los elementos del proyecto que se muestran en el cuadro de diálogo del asistente **Agregar nuevo elemento.** |
| Val SortPriority | REG_DWORD | 100[!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]( ) | Determina el criterio de ordenación en el nodo de árbol de los archivos que se muestran en el cuadro de diálogo **Agregar nuevo elemento.** |

> [!NOTE]
> Los GUID para los tipos de proyecto de Visual C- y Visual Basic son los siguientes:
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: FAE04EC0-301F-11D3-BF4B-00C04F79EFBC
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: F184B08F-C81C-45F6-A57F-5ABD9991F28F

 El directorio que aparece para **TemplatesDir**, que es *%TEMPLATE_PATH%\\&lt;&gt;SomeProjectItems*, es el nodo en el lado izquierdo del árbol del cuadro de diálogo Agregar nuevo **elemento** . Los elementos adicionales del árbol se basan en el subdirectorio dentro de ese directorio raíz. Los archivos disponibles para agregar al proyecto son los elementos del panel derecho del cuadro de diálogo **Agregar nuevo elemento.**

 Normalmente, esta carpeta contendrá los archivos de plantilla para el proyecto, como un archivo HTML o *.cpp* de plantilla, y cualquier archivo *.vsz* para iniciar asistentes. Para controlar cómo se muestran los elementos, también puede incluir archivos *.vsdir* para localizar nombres de directorio e iconos. La cadena localizada es el título que aparece en el cuadro de diálogo que representa este nodo en el árbol del cuadro de diálogo **Agregar nuevo elemento.**

 Sin embargo, no es necesario tener todo en un archivo *.vsdir.* Puede tener un archivo *.vsdir* para cada elemento del directorio. Para obtener más información, vea [Archivos del asistente (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) y Archivos de descripción del directorio de plantilla [(.vsdir).](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

> [!NOTE]
> Los archivos *.vsdir* de los directorios de plantilla son opcionales. Si solo desea colocar un elemento de proyecto en el directorio y mostrarlo en el cuadro de diálogo **Agregar nuevo elemento,** puede colocar ese archivo en el directorio templates especificado en la instrucción **TemplatesDir.** El archivo se mostrará en el panel derecho del cuadro de diálogo **Agregar nuevo elemento** para ese proyecto. Sin embargo, si desea mostrar un título localizado para el archivo o un icono, debe incluir al menos un archivo *.vsdir* en el directorio templates.

## <a name="group-project-items"></a>Elementos de proyecto de grupo
 Si desea contener grupos de plantillas en carpetas en el árbol del cuadro de diálogo **Agregar nuevo elemento,** debe tener subdirectorios en el directorio de plantilla raíz con los elementos en ellos. Cuando se muestra el cuadro de diálogo **Agregar nuevo elemento** a los usuarios, también verán las subcarpetas y podrán seleccionar elementos del proyecto de ellos.

 La prioridad de ordenación en el segmento de código determina dónde se creará este directorio de plantilla en el árbol en relación con otros elementos del nodo de árbol. Para el cuadro de diálogo **Agregar nuevo elemento,** la prioridad de ordenación es todo lo que debe incluir para que los elementos se muestren en la ubicación correcta en el cuadro de diálogo.

 También puede implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> la interfaz para filtrar lo que se muestra en el cuadro de diálogo **Agregar nuevo elemento.** Al implementar esta interfaz, puede configurar un directorio de plantilla en el disco que contenga, por ejemplo, 50 archivos de plantilla y asistente. De este modo, puede tener diferentes tipos de proyecto con 20 archivos que pertenecen a un tipo de proyecto, los otros 30 archivos que pertenecen a otro tipo de proyecto y todos los archivos disponibles en un tipo general de proyecto. De esta manera, dependiendo de la plantilla de proyecto que se cree, puede mostrar un conjunto diferente de archivos de plantilla.

 Por ejemplo, en un proyecto de Visual Basic, es posible que tenga proyectos web y proyectos de cliente. Los formularios web no son elementos útiles para agregar a un proyecto de cliente y los formularios de Windows no son elementos útiles para agregar a un proyecto de servidor web. Por lo tanto, puede crear un directorio de plantilla que contenga todos los archivos para ambos tipos de proyecto. A continuación, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>mediante la implementación de , puede ocultar elementos que no se deben mostrar en función del tipo de proyecto o configuración del proyecto en el proyecto.

## <a name="filter-project-items"></a>Filtrar elementos de proyecto
 `IVsFilterAddProjectItemDlg2`proporciona filtrado de elementos en el árbol (panel izquierdo) y archivos de proyecto (panel derecho) de las siguientes maneras:

- Por los nombres localizados (los subtítulos que se muestran en el `IVsFilterAddProjectItemDlg`cuadro de diálogo que se encuentra en el archivo *.vsdir)* proporcionado por .

- Por los nombres reales de los archivos y carpetas en el disco `IVsFilterAddProjectItemDlg`(no localizado — sin archivo *.vsdir)* proporcionado por .

- Por categoría, `IVsFilterAddProjectItemDlg2`proporcionada por .

  Para filtrar por categoría, proporcione una cadena de categoría a un elemento del archivo *.vsdir,* como *el formulario web* o el elemento de *cliente* en Visual Basic. A continuación, el código del cuadro de diálogo recupera la clasificación de categoría del archivo *.vsdir* y se la pasa. A continuación, puede pasar esa información a la implementación de filtrar el **Agregar nuevo elemento** cuadro de `IVsFilterAddProjectItemDlg2` diálogo por categorías. También puede filtrar elementos para páginas Web o como casos de aplicación Win32 de cliente. Además, puede [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] identificar elementos etiquetados como microsoft Foundation Classes (MFC) o elementos de biblioteca de plantillas activas (ATL). Al identificar estas posiciones, el sistema de proyectos puede definir sus propias clasificaciones para que el sistema se pueda filtrar en función de categorías y clasificaciones.

  Si implementa esta funcionalidad de filtro, no tiene que asignar una tabla de cada elemento que se debe ocultar. Simplemente puede clasificar elementos en tipos y colocar las clasificaciones en el archivo o archivos *.vsdir.* A continuación, puede ocultar cualquiera de los elementos que tienen una clasificación específica mediante la implementación de la interfaz. De este modo, puede hacer que los elementos del cuadro de diálogo **Agregar nuevo elemento** sean dinámicos en función del estado del proyecto.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Registrar plantillas de proyectos y elementos](../../extensibility/internals/registering-project-and-item-templates.md)
- [CATID para objetos que se utilizan normalmente para extender proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [Agregar plantillas de proyecto y elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Archivos de descripción del directorio de plantillas (.vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [Archivo Wizard (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
