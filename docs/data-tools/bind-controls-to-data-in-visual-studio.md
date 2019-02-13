---
title: Enlazar controles a datos
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- displaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 32b392f59fb0ac587730d2aa432ca11d91d5a9ea
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55939767"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Enlazar controles a los datos en Visual Studio

Para mostrar los datos a los usuarios de la aplicación, puede enlazarlos a controles. Puede crear estos controles enlazados a datos arrastrando elementos desde la **orígenes de datos** ventana a una superficie de diseño o controles en una superficie en Visual Studio.

En este tema se describen los orígenes de datos que puede utilizar para crear controles enlazados a datos. También se describen algunas de las tareas generales implicadas en el enlace de datos. Para obtener detalles concretos sobre cómo crear controles enlazados a datos, vea [controla el enlace Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) y [WPF enlazar controles a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

## <a name="data-sources"></a>Orígenes de datos

En el contexto de enlace de datos, un origen de datos representa los datos en memoria que se puede enlazar a la interfaz de usuario. En términos prácticos, un origen de datos puede ser una clase de Entity Framework, un conjunto de datos, un punto de conexión de servicio que se encapsula en un objeto de proxy. NET, una clase LINQ to SQL, o cualquier objeto .NET o colección. Algunos orígenes de datos permiten crear controles enlazados a datos arrastrando los elementos de la ventana **Orígenes de datos**, mientras que otros no lo permiten. En la tabla siguiente se muestran los orígenes de datos que se admiten.

| Origen de datos | Compatibilidad con arrastrar y colocar en el **Diseñador de Windows Forms** | Compatibilidad con arrastrar y colocar en **WPF Designer** | Compatibilidad con arrastrar y colocar en el **Diseñador de Silverlight** |
| - | - | - | - |
| Conjunto de datos | Sí | Sí | No |
| Entity Data Model | Sí<sup>1</sup> | Sí | Sí |
| Clases LINQ to SQL | No<sup>2</sup> | No<sup>2</sup> | No<sup>2</sup> |
| Servicios como [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], servicios WCF y servicios Web | Sí | Sí | Sí |
| Object | Sí | Sí | Sí |
| SharePoint | Sí | Sí | Sí |

1. Generar el modelo mediante el **Entity Data Model** asistente, a continuación, arrastrar esos objetos al diseñador.

2. Las clases LINQ to SQL no aparecen en la ventana **Orígenes de datos**. Sin embargo, puede agregar un nuevo origen de datos de objeto basado en clases LINQ to SQL y, a continuación, arrastrar esos objetos al diseñador para crear los controles enlazados a datos. Para obtener más información, consulte [Tutorial: crear clases de LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="data-sources-window"></a>Ventana de orígenes de datos

Los orígenes de datos están disponible para su proyecto como elementos en la ventana **Orígenes de datos**. Esta ventana está visible cuando una superficie de diseño del formulario es la ventana activa en el proyecto, o bien puede abrirla (cuando se abre un proyecto) eligiendo **vista** > **Other Windows**  >   **Orígenes de datos**. Puede arrastrar elementos desde esta ventana para crear controles enlazados a los datos subyacentes y también puede configurar los orígenes de datos con el botón secundario.

![Ventana de orígenes de datos](../data-tools/media/raddata-data-sources-window.png)

Por cada tipo de datos que aparece en la ventana **Orígenes de datos**, se crea un control predeterminado al arrastrar el elemento hasta el diseñador. Antes de arrastrar un elemento desde el **orígenes de datos** ventana, puede cambiar el control que se crea. Para obtener más información, consulte [establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Tareas necesarias para enlazar controles a datos

En la tabla siguiente se enumera algunas de las tareas más comunes que realizar para enlazar controles a datos.

|Tarea|Más información|
|----------| - |
|Abra la ventana **Orígenes de datos**.|Abra una superficie de diseño en el editor y elija **vista** > **orígenes de datos**.|
|Agregue un origen de datos al proyecto.|[Agregar nuevos orígenes de datos](../data-tools/add-new-data-sources.md)|
|Establezca el control que se crea cuando se arrastra un elemento de la ventana **Orígenes de datos** al diseñador.|[Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Modifique la lista de controles que están asociados a elementos en la ventana **Orígenes de datos**.|[Agregar controles personalizados a la ventana Orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Crear controles enlazados a datos.|[Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Enlace de controles de WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|
|Enlazar a un objeto o colección.|[Enlazar objetos en Visual Studio](../data-tools/bind-objects-in-visual-studio.md)|
|Filtrar los datos que aparece en la interfaz de usuario.|[Filtrar y ordenar los datos en una aplicación Windows Forms](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Personalizar títulos para los controles.|[Personalizar el modo en que Visual Studio crea los títulos de controles enlazados a datos](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Vea también

- [Visual Studio Data Tools para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Windows Forms data binding](/dotnet/framework/winforms/windows-forms-data-binding) (Enlace de datos de Windows Forms)