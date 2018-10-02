---
title: Enlazar controles a datos en Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- dislaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 85bfcb03ea2f383d8f1517d17c866c2320891aaa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578502"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Enlazar controles a datos en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [enlazar controles a datos en Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).  
  
  
Para mostrar los datos a los usuarios de la aplicación, puede enlazarlos a controles. Puede crear estos controles enlazados a datos arrastrando elementos desde la **orígenes de datos** ventana a una superficie de diseño o controles en una superficie en Visual Studio.  
  
 En este tema se describen los orígenes de datos que puede utilizar para crear controles enlazados a datos. También se describen algunas de las tareas generales implicadas en el enlace de datos. Para obtener detalles concretos sobre cómo crear controles enlazados a datos, vea [controla el enlace Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) y [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
## <a name="data-sources"></a>Orígenes de datos  
 En el contexto de enlace de datos, un origen de datos representa los datos en memoria que se puede enlazar a la interfaz de usuario. En términos prácticos, un origen de datos puede ser una clase de Entity Framework, un conjunto de datos, un punto de conexión de servicio que se encapsula en un objeto de proxy. NET, una clase LINQ to SQL, o cualquier objeto .NET o colección. Algunos orígenes de datos le permiten crear controles enlazados a datos arrastrando elementos desde la **orígenes de datos** ventana, mientras que otros orígenes de datos no. En la tabla siguiente se muestran los orígenes de datos que se admiten.  
  
|Origen de datos|Compatibilidad con arrastrar y colocar en **el Diseñador de Windows Forms**|Compatibilidad con arrastrar y colocar en **WPF Designer**|Compatibilidad con arrastrar y colocar en **Silverlight Designer**|  
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|  
|Conjunto de datos|Sí|Sí|No|  
|Entity Data Model|Sí<sup>1</sup>|Sí|Sí|  
|Clases LINQ to SQL|No<sup>2</sup>|No<sup>2</sup>|No<sup>2</sup>|  
|Servicios (incluido [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], WCF services y servicios web)|Sí|Sí|Sí|  
|Object|Sí|Sí|Sí|  
|SharePoint|Sí|Sí|Sí|  
  
 1. Generar el modelo mediante el **Entity Data Model** asistente, a continuación, arrastrar esos objetos al diseñador.  
  
 2. Clases LINQ to SQL no aparecen en la **orígenes de datos** ventana. Sin embargo, puede agregar un nuevo origen de datos de objeto basado en clases LINQ to SQL y, a continuación, arrastrar esos objetos al diseñador para crear los controles enlazados a datos. Para obtener más información, consulte [Tutorial: crear clases de LINQ to SQL (Object Relational Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
## <a name="data-sources-window"></a>Ventana de orígenes de datos  
 Orígenes de datos están disponibles para su proyecto como elementos en el **orígenes de datos** ventana. Esta ventana está visible o accesible desde el **vista** menú, cuando una superficie de diseño del formulario es la ventana activa en el proyecto. Puede arrastrar elementos desde esta ventana para crear controles enlazados a los datos subyacentes y también puede configurar los orígenes de datos con el botón secundario.  
  
 ![Ventana Orígenes de datos](../data-tools/media/raddata-data-sources-window.png "raddata ventana de orígenes de datos")  
  
 Para cada tipo de datos que aparece en el **orígenes de datos** ventana, se crea un control de forma predeterminada cuando se arrastra el elemento hasta el diseñador. Antes de arrastrar un elemento desde el **orígenes de datos** ventana, puede cambiar el control que va a crear. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="tasks-involved-in-binding-controls-to-data"></a>Tareas necesarias para enlazar controles a los datos  
 En la tabla siguiente se enumera algunas de las tareas más comunes que realizar para enlazar controles a datos.  
  
|Tarea|Más información|  
|----------|----------------------|  
|Abra el **orígenes de datos** ventana.|Abra una superficie de diseño en el editor y elija **vista** > **orígenes de datos**.|  
|Agregar un origen de datos al proyecto.|[Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)|  
|Establecer el control que se crea al arrastrar un elemento desde el **orígenes de datos** ventana al diseñador.|[Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|  
|Modificar la lista de controles que están asociados con los elementos de la **orígenes de datos** ventana.|[Agregar controles personalizados a la ventana Orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md)|  
|Crear controles enlazados a datos.|[Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Enlace de controles de WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)|  
|Enlazar a un objeto o colección.|[Enlazar objetos en Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|  
|Filtrar los datos que aparece en la interfaz de usuario.|[Filtrar y ordenar los datos en una aplicación Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|  
|Personalizar títulos para los controles.|[Personalizar el modo en que Visual Studio crea los títulos de controles enlazados a datos](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|  
  
## <a name="see-also"></a>Vea también  
 [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [Enlace de datos en Windows Forms](http://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)

