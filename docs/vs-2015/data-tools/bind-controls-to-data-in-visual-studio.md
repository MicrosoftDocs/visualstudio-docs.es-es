---
title: Enlazar controles a datos
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- displaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 31e2086126e9a17554c80b53858205e83fd504fd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72673034"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Enlazar controles a los datos en Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para mostrar los datos a los usuarios de la aplicación, puede enlazarlos a controles. Puede crear estos controles enlazados a datos arrastrando elementos desde la ventana **orígenes de datos** hasta una superficie de diseño o controles en una superficie de Visual Studio.

 En este tema se describen los orígenes de datos que puede utilizar para crear controles enlazados a datos. También se describen algunas de las tareas generales implicadas en el enlace de datos. Para obtener detalles más específicos sobre cómo crear controles enlazados a datos, vea [enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) y [enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="data-sources"></a>Orígenes de datos
 En el contexto del enlace de datos, un origen de datos representa los datos en memoria que se pueden enlazar a la interfaz de usuario. En términos prácticos, un origen de datos puede ser una clase Entity Framework, un conjunto de datos, un punto de conexión de servicio encapsulado en un objeto proxy .NET, una clase LINQ to SQL o cualquier objeto o colección .NET. Algunos orígenes de datos permiten crear controles enlazados a datos arrastrando los elementos de la ventana **Orígenes de datos**, mientras que otros no lo permiten. En la tabla siguiente se muestran los orígenes de datos que se admiten.

|Origen de datos|Compatibilidad con arrastrar y colocar en el **Diseñador de Windows Forms**|Compatibilidad con arrastrar y colocar en **WPF Designer**|Compatibilidad con arrastrar y colocar en el **Diseñador de Silverlight**|
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|
|Conjunto de datos|Sí|Sí|No|
|Entity Data Model|Sí<sup>1</sup>|Sí|Sí|
|Clases LINQ to SQL|No<sup>2</sup>|No<sup>2</sup>|No<sup>2</sup>|
|Servicios como [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)], servicios WCF y servicios Web|Sí|Sí|Sí|
|Object|Sí|Sí|Sí|
|SharePoint|Sí|Sí|Sí|

 1. Genere el modelo con el Asistente para **Entity Data Model** y, a continuación, arrastre esos objetos al diseñador.

 2. Las clases LINQ to SQL no aparecen en la ventana **Orígenes de datos**. Sin embargo, puede agregar un nuevo origen de datos de objeto basado en clases LINQ to SQL y, a continuación, arrastrar esos objetos al diseñador para crear los controles enlazados a datos. Para obtener más información, vea [Tutorial: crear clases de LINQ to SQL (Object](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)Relational Designer).

## <a name="data-sources-window"></a>Ventana de orígenes de datos
 Los orígenes de datos están disponible para su proyecto como elementos en la ventana **Orígenes de datos**. Esta ventana está visible o es accesible desde el menú **Ver** cuando una superficie de diseño de formulario es la ventana activa del proyecto. Puede arrastrar elementos desde esta ventana para crear controles enlazados a los datos subyacentes, y también puede configurar los orígenes de datos haciendo clic con el botón secundario.

 ![Ventana orígenes de datos](../data-tools/media/raddata-data-sources-window.png "raddata ventana orígenes de datos")

 Por cada tipo de datos que aparece en la ventana **Orígenes de datos**, se crea un control predeterminado al arrastrar el elemento hasta el diseñador. Antes de arrastrar un elemento desde la ventana **orígenes de datos** , puede cambiar el control que se creará. Para obtener más información, vea [establecer el control que se creará al arrastrar desde la ventana orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Tareas necesarias para enlazar controles a datos
 En la tabla siguiente se enumeran algunas de las tareas más comunes que se realizan para enlazar controles a datos.

|Tarea|Más información|
|----------|----------------------|
|Abra la ventana **Orígenes de datos**.|Abra una superficie de diseño en el editor y elija **ver**  > **orígenes de datos**.|
|Agregue un origen de datos al proyecto.|[Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)|
|Establezca el control que se crea cuando se arrastra un elemento de la ventana **Orígenes de datos** al diseñador.|[Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Modifique la lista de controles que están asociados a elementos en la ventana **Orígenes de datos**.|[Agregar controles personalizados a la ventana Orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Crear controles enlazados a datos.|[Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Enlace de controles de WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)|
|Enlazar a un objeto o una colección.|[Enlazar objetos en Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|
|Filtre los datos que aparecen en la interfaz de usuario.|[Filtrar y ordenar los datos en una aplicación Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Personalizar títulos para los controles.|[Personalizar el modo en que Visual Studio crea los títulos de controles enlazados a datos](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Vea también
 Enlace [de datos de Visual Studio Data Tools para .net](../data-tools/visual-studio-data-tools-for-dotnet.md) [Windows Forms](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa)
