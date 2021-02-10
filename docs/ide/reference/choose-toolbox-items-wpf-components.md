---
title: Elegir elementos del cuadro de herramientas, Componentes de WPF
description: Aprenda a usar la pestaña Componentes de WPF para mostrar los controles de Windows Presentation Foundation que puede seleccionar en el equipo local.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d23418cd784b9e0b7c916c1e5629a6da012b9d0b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836402"
---
# <a name="choose-toolbox-items-wpf-components"></a>Elegir elementos del Cuadro de herramientas, componentes de WPF

En esta pestaña del cuadro de diálogo **Elegir elementos del cuadro de herramientas**, se muestra una lista de controles de Windows Presentation Foundation (WPF) disponibles en el equipo local. Para mostrar esta lista, seleccione **Elegir elementos del cuadro de herramientas** del menú **Herramientas** para mostrar el cuadro de diálogo **Elegir elementos del cuadro de herramientas** y después seleccione la pestaña **Componentes WPF**. Para ordenar los componentes de la lista, seleccione cualquier encabezado de columna.

- Cuando se seleccione la casilla junto a un componente, se mostrará un icono de ese componente en el **cuadro de herramientas**.

    > [!TIP]
    > Para agregar un control de WPF a un documento del proyecto abierto para su edición, arrastre su icono de **Cuadro de herramientas** a la superficie de la vista Diseño. El marcado y el código predeterminados del componente se insertan en el proyecto, preparados para que los pueda modificar. Para obtener más información, vea [Cuadro de herramientas](../../ide/reference/toolbox.md).

- Cuando se desactive la casilla junto a un componente, el icono correspondiente se quitará del **Cuadro de herramientas**.

    > [!NOTE]
    > Los componentes de .NET instalados en el equipo siguen estando disponibles aunque no se muestren sus iconos en el **Cuadro de herramientas**.

Las columnas de la pestaña **Componentes WPF** contienen la siguiente información:

**Nombre**

Enumera los nombres de los controles de WPF para los que existen entradas en el Registro del equipo.

**Namespace**

Muestra la jerarquía del espacio de nombres de la [API de .NET](/dotnet/api/?view=netframework-4.7&preserve-view=true) que define la estructura del componente. Ordene esta columna para mostrar los componentes disponibles en cada espacio de nombres de .NET instalado en el equipo.

**Nombre del ensamblado**

Muestra el nombre del ensamblado de .NET que incluye el espacio de nombres de cada componente. Ordene esta columna para mostrar los espacios de nombres incluidos en cada ensamblado de .NET instalado en el equipo.

**Directorio**

Muestra la ubicación del ensamblado de .NET. La ubicación predeterminada de todos los ensamblados es la caché global de ensamblados. Para más información sobre la caché global de ensamblados, consulte [Trabajar con ensamblados y la caché global de ensamblados](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac).

## <a name="uielement-list"></a>Lista de UIElement

### <a name="filter"></a>Filter

Filtra la lista de controles de WPF según la cadena proporcionada en el cuadro de texto. Se muestran todas las coincidencias encontradas en cualquiera de las cuatro columnas.

**Borrar**

Borra la cadena de filtro.

**Browse**

Abre el cuadro de diálogo **Abrir**, que le permite ir a ensamblados que contienen controles de WPF. Úselo para cargar ensamblados que no se encuentran en la caché global de ensamblados.

**Lenguaje**

Muestra el lenguaje localizado del ensamblado que contiene el control de WPF seleccionado.

## <a name="limitations"></a>Limitaciones

La acción de agregar un control personalizado o <xref:System.Windows.Controls.UserControl> al cuadro de herramientas tiene las limitaciones siguientes:

- Solo funciona con los controles personalizados definidos fuera del proyecto actual.

- No se actualiza correctamente al cambiar la configuración de soluciones de Depuración a Lanzamiento ni de Lanzamiento a Depuración. Esto se debe a que la referencia no es una referencia de proyecto, sino para el ensamblado en el disco. Si el control forma parte de la solución actual, al cambiar de Depuración a Lanzamiento, el proyecto sigue haciendo referencia a la versión de depuración del control.

Además, si se aplican metadatos en tiempo de diseño al control personalizado y estos especifican que el atributo [Microsoft.Windows.Design.ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) se establece en `false`, el control no aparece en el Cuadro de herramientas.

Puede hacer referencia a los controles directamente en la vista XAML mediante la asignación del espacio de nombres y el ensamblado para el control.

## <a name="see-also"></a>Consulte también

- [Cuadro de herramientas](../../ide/reference/toolbox.md)
- [Introducción a WPF](../../designers/getting-started-with-wpf.md)
