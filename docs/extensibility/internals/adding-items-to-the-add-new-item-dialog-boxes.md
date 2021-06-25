---
title: Agregar elementos a los cuadros de diálogo Agregar nuevo elemento | Microsoft Docs
description: Obtenga información sobre cómo agregar elementos al cuadro de diálogo Agregar nuevo elemento de Visual Studio, para que pueda mostrar plantillas y elementos de proyecto para su uso en los proyectos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 70bc1a0c4d90d8cab0b2193550773745fc2dd47e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904414"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Agregar elementos al cuadro de diálogo Agregar nuevo elemento
El proceso para agregar elementos al cuadro **de diálogo Agregar** nuevo elemento comienza con las claves del Registro. Como se muestra en las siguientes entradas del Registro, la sección **AddItemTemplates** contiene  la ruta de acceso y el nombre del directorio en el que se ponen los elementos disponibles en el cuadro de diálogo Agregar nuevo elemento.

> [!NOTE]
> La tabla inmediatamente posterior al segmento de código contiene información adicional sobre la entrada del Registro.

 Esta sección se encuentra en **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects**.

 El primer GUID es el CLSID para proyectos de este tipo; El segundo GUID indica el tipo de proyecto registrado para las plantillas Agregar elementos:

 **\\{C061DB26-5833-11D2-96F5-00000000000} \\ AddItemTemplates \\ TemplatesDir \\ {ACEF4EB2-57CF-11D2-96F4-00000000000} \\ 1**

 **@** = #6

   =  \\ TemplatesDir &lt; Visual Studio de instalación del SDK &gt; \\ vsIntegration \\ &lt; SomeFolder &gt; \\ &lt; SomePackage &gt; \\ &lt; SomeProject &gt; \\ &lt; SomeProjectItems&gt;

 **SortPriority** = dword:00000064

| Nombre | Tipo | Datos (del *archivo .rgs)* | Descripción |
|------------------|-----------| - | - |
| @ (valor predeterminado) | REG_SZ | #%IDS_ADDITEM_TEMPLATES_ENTRY% | Id. de recurso **para agregar plantillas de** elemento. |
| Plantillas de ValDir | REG_SZ | %TEMPLATE_PATH% \\ &lt; SomeProjectItems&gt; | Ruta de acceso de los elementos de proyecto que se muestran en el cuadro de diálogo del **Asistente para agregar nuevo** elemento. |
| Val SortPriority | REG_DWORD | 100 ( [!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)] ) | Determina el criterio de ordenación en el nodo de árbol de los archivos que se muestran en el **cuadro de diálogo Agregar nuevo** elemento . |

> [!NOTE]
> Los GUID de visual C# y Visual Basic de proyecto son los siguientes:
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}

 El directorio enumerado para **TemplatesDir**, que es *%TEMPLATE_PATH% \\ &lt; SomeProjectItems &gt;*, es  el nodo del lado izquierdo del árbol de cuadro de diálogo Agregar nuevo elemento. Los elementos adicionales del árbol se basan en el subdirectorio dentro de ese directorio raíz. Los archivos disponibles para agregarse al proyecto son los elementos del panel derecho del **cuadro de diálogo** Agregar nuevo elemento .

 Normalmente, esta carpeta contendrá los archivos de plantilla para el proyecto, como un archivo HTML o *.cpp* de plantilla, y cualquier *archivo .vsz* para los asistentes de inicio. Para controlar cómo se muestran los elementos, también puede incluir *archivos .vsdir* para la localización de iconos y nombres de directorio. La cadena localizada es el título que aparece en el cuadro de diálogo que representa este nodo en el **árbol de cuadro de diálogo Agregar** nuevo elemento.

 Sin embargo, no es necesario tener todo en un *archivo .vsdir.* Puede tener un archivo *.vsdir* para cada elemento del directorio. Para obtener más información, vea [Archivo del Asistente (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) y Archivos de descripción del directorio de plantilla [(.vsdir).](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

> [!NOTE]
> Los *archivos .vsdir* de los directorios de plantilla son opcionales. Si solo quiere colocar un elemento de proyecto en  el directorio y mostrarlo en el cuadro de diálogo Agregar nuevo elemento, puede colocar ese archivo en el directorio templates especificado en la **instrucción TemplatesDir.** A continuación, el archivo se mostrará en el panel derecho del cuadro de diálogo **Agregar** nuevo elemento para ese proyecto. Sin embargo, si desea mostrar un título localizado para el archivo o un icono, debe incluir al menos un *archivo .vsdir* en el directorio templates.

## <a name="group-project-items"></a>Agrupar elementos de proyecto
 Si desea contener grupos de plantillas  en carpetas en el árbol de cuadro de diálogo Agregar nuevo elemento, debe tener subdirectorios en el directorio raíz de la plantilla con los elementos que contienen. Cuando se **muestre el cuadro de diálogo** Agregar nuevo elemento a los usuarios, también verán las subcarpetas y podrán seleccionar elementos del proyecto de ellos.

 La prioridad de ordenación en el segmento de código determina dónde se creará este directorio de plantilla en el árbol con respecto a otros elementos del nodo de árbol. En el **cuadro de diálogo** Agregar nuevo elemento, la prioridad de ordenación es todo lo que debe incluir para que los elementos se muestren en la ubicación correcta del cuadro de diálogo.

 También puede implementar la interfaz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> para filtrar lo que se muestra en el cuadro de diálogo Agregar **nuevo** elemento . Al implementar esta interfaz, puede configurar un directorio de plantilla en el disco que contenga, por ejemplo, 50 archivos de plantilla y asistente. De este modo, puede tener diferentes tipos de proyecto con 20 archivos que pertenecen a un tipo de proyecto, los otros 30 archivos que pertenecen a otro tipo de proyecto y todos los archivos disponibles en un tipo general de proyecto. De esta manera, en función de la plantilla de proyecto que se cree, puede mostrar un conjunto diferente de archivos de plantilla.

 Por ejemplo, en un Visual Basic, es posible que tenga proyectos web y proyectos de cliente. Los formularios web no son elementos útiles para agregar a un proyecto de cliente y los formularios Windows Forms no son elementos útiles para agregar a un proyecto de servidor web. Por lo tanto, puede crear un directorio de plantilla que contenga todos los archivos para ambos tipos de proyecto. A continuación, mediante la implementación de , puede ocultar elementos que no se deben mostrar en función del tipo de configuración del proyecto <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> o del proyecto.

## <a name="filter-project-items"></a>Filtrar elementos de proyecto
 `IVsFilterAddProjectItemDlg2` proporciona el filtrado de elementos en el árbol (panel izquierdo) y los archivos de proyecto (panel derecho) de las maneras siguientes:

- Por los nombres localizados (títulos que se muestran en el cuadro de diálogo que se encuentra en el *archivo .vsdir)* proporcionados por `IVsFilterAddProjectItemDlg` .

- Por los nombres reales de los archivos y carpetas del disco (no localizados , sin *archivo .vsdir)* proporcionados por `IVsFilterAddProjectItemDlg` .

- Por categoría, proporcionada por `IVsFilterAddProjectItemDlg2` .

  Para filtrar por categoría, proporcione una cadena de categoría a un elemento del archivo *.vsdir,* como *formulario web* o elemento *cliente* en Visual Basic. A continuación, el código del cuadro de diálogo recupera la clasificación de categorías del *archivo .vsdir* y la pasa a usted. Después, puede pasar esa información a la implementación de para filtrar el cuadro de diálogo Agregar `IVsFilterAddProjectItemDlg2` **nuevo** elemento por categorías. También puede filtrar elementos para páginas web o como casos de aplicación Win32 de cliente. Además, puede identificar elementos [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] etiquetados como elementos Microsoft Foundation Classes (MFC) o de biblioteca de plantillas activas (ATL). Al identificar estos elementos, el sistema del proyecto puede definir sus propias clasificaciones para que el sistema se pueda filtrar en función de categorías y clasificaciones.

  Si implementa esta funcionalidad de filtro, no tiene que asignar una tabla de todos los elementos que deben estar ocultos. Simplemente puede clasificar elementos en tipos y colocar las clasificaciones en el archivo o archivos *.vsdir.* A continuación, puede ocultar cualquiera de los elementos que tienen una clasificación específica mediante la implementación de la interfaz . De este modo, puede hacer  que los elementos del cuadro de diálogo Agregar nuevo elemento sea dinámicos en función del estado del proyecto.

## <a name="see-also"></a>Consulta también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Registro de plantillas de proyecto y elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [CATID para objetos que se usan normalmente para ampliar proyectos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [Agregar plantillas de proyecto y elemento de proyecto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Archivos de descripción del directorio de plantilla (.vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [Archivo del asistente (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
