---
title: Elegir elementos del cuadro de herramientas, Componentes de WPF | Microsoft Docs
ms.custom: ''
ms.date: 06/21/2017
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 955d0ab74d59606e63a4772aee5de96c920544ed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="choose-toolbox-items-wpf-components"></a>Elegir elementos del Cuadro de herramientas, componentes de WPF

En esta pestaña del cuadro de diálogo **Elegir elementos del cuadro de herramientas**, se muestra una lista de controles de Windows Presentation Foundation (WPF) disponibles en el equipo local. Para mostrar esta lista, seleccione **Elegir elementos del cuadro de herramientas** del menú **Herramientas** para mostrar el cuadro de diálogo **Elegir elementos del cuadro de herramientas** y después seleccione la pestaña **Componentes WPF**. Para ordenar los componentes de la lista, seleccione cualquier encabezado de columna.

- Cuando se seleccione la casilla junto a un componente, se mostrará un icono de ese componente en el **cuadro de herramientas**.

    > [!TIP]
    > Para agregar un control de WPF a un documento del proyecto abierto para su edición, arrastre su icono de **Cuadro de herramientas** a la superficie de la vista Diseño. El marcado y el código predeterminados del componente se insertan en el proyecto, preparados para que los pueda modificar. Para obtener más información, vea [Cuadro de herramientas](../../ide/reference/toolbox.md).

- Cuando se desactive la casilla junto a un componente, el icono correspondiente se quitará del **Cuadro de herramientas**.

    > [!NOTE]
    > Los componentes de .NET Framework instalados en el equipo siguen estando disponibles aunque no se muestren sus iconos en el **cuadro de herramientas**.

Las columnas de la pestaña **Componentes WPF** contienen la siguiente información:

nombre  
Enumera los nombres de los controles de WPF para los que existen entradas en el Registro del equipo.

Espacio de nombres  
Muestra la jerarquía del espacio de nombres de la [API de clases de .NET Framework](/dotnet/api/?view=netframework-4.7) que define la estructura del componente. Ordene esta columna para mostrar los componentes disponibles en cada espacio de nombres de .NET Framework instalado en el equipo.

Nombre del ensamblado  
Muestra el nombre del ensamblado de .NET Framework que incluye el espacio de nombres de cada componente. Ordene esta columna para mostrar los espacios de nombres contenidos en cada ensamblado de .NET Framework instalado en el equipo.

Directorio  
Muestra la ubicación del ensamblado de .NET Framework. La ubicación predeterminada de todos los ensamblados es la caché global de ensamblados. Para obtener más información sobre la caché global de ensamblados, consulte [Trabajar con ensamblados y la caché global de ensamblados](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac).

## <a name="uielement-list"></a>Lista de UIElement

### <a name="filter"></a>Filtro

Filtra la lista de controles de WPF según la cadena proporcionada en el cuadro de texto. Se muestran todas las coincidencias encontradas en cualquiera de las cuatro columnas.

### <a name="clear"></a>Clear

Borra la cadena de filtro.

### <a name="browse"></a>Examinar

Abre el cuadro de diálogo **Abrir**, que le permite ir a ensamblados que contienen controles de WPF. Úselo para cargar ensamblados que no se encuentran en la caché global de ensamblados.

### <a name="language"></a>Lenguaje

Muestra el lenguaje localizado del ensamblado que contiene el control de WPF seleccionado.

## <a name="limitations"></a>Limitaciones

La acción de agregar un control personalizado o <xref:System.Windows.Controls.UserControl> al cuadro de herramientas tiene las limitaciones siguientes:

- Solo funciona con los controles personalizados definidos fuera del proyecto actual.

- No se actualiza correctamente al cambiar la configuración de soluciones de Depuración a Lanzamiento ni de Lanzamiento a Depuración. Esto se debe a que la referencia no es una referencia de proyecto, sino para el ensamblado en el disco. Si el control forma parte de la solución actual, al cambiar de Depuración a Lanzamiento, el proyecto sigue haciendo referencia a la versión de depuración del control.

Además, si se aplican metadatos en tiempo de diseño al control personalizado y estos especifican que el atributo <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> se establece en `false`, el control no aparece en el cuadro de herramientas.

Puede hacer referencia a los controles directamente en la vista XAML mediante la asignación del espacio de nombres y el ensamblado para el control.

## <a name="see-also"></a>Vea también

[Cuadro de herramientas](../../ide/reference/toolbox.md)  
[Introducción a WPF](../../designers/getting-started-with-wpf.md)
