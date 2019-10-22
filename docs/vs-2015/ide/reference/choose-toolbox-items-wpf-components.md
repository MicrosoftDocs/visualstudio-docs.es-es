---
title: Elegir elementos del cuadro de herramientas, Componentes de WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5c7967635d8e5d64907587fcd1a9b4d84a31d569
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660918"
---
# <a name="choose-toolbox-items-wpf-components"></a>Elegir elementos del cuadro de herramientas, Componentes de WPF
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En esta pestaña del cuadro de diálogo **Elegir elementos del cuadro de herramientas**, se muestra una lista de controles de Windows Presentation Foundation (WPF) disponibles en el equipo local. Para mostrar esta lista, seleccione **Elegir elementos del cuadro de herramientas** del menú **Herramientas** para mostrar el cuadro de diálogo **Elegir elementos del cuadro de herramientas** y después seleccione la pestaña **Componentes WPF**. Para ordenar los componentes de la lista, seleccione cualquier encabezado de columna.

- Cuando se seleccione la casilla junto a un componente, se mostrará un icono de ese componente en el **cuadro de herramientas**.

  > [!TIP]
  > Para agregar una instancia de un control de WPF a un documento del proyecto abierto para su edición, arrastre su icono de **cuadro de herramientas** a la superficie de la vista Diseño. El marcado y el código predeterminados del componente se insertan en el proyecto, preparados para que los pueda modificar. Para obtener más información, consulte [Cómo: Administrar la ventana Cuadro de herramientas](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2) y [Cómo: Manipular fichas del cuadro de herramientas](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

- Cuando se desactive la casilla junto a un componente, el icono correspondiente se quitará del **cuadro de herramientas.**

  > [!NOTE]
  > Los componentes de .NET Framework instalados en el equipo siguen estando disponibles aunque no se muestren sus iconos en el **cuadro de herramientas**.

  Las columnas de la pestaña **Componentes WPF** contienen la siguiente información:

  Nombre muestra los nombres de los controles de WPF para los que existen entradas en el registro del equipo.

  Espacio de nombres muestra la jerarquía del espacio de nombres de la [biblioteca de clases NIB: .NET Framework](https://msdn.microsoft.com/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29) que define la estructura del componente. Ordene esta columna para mostrar los componentes disponibles en cada espacio de nombres de .NET Framework instalado en el equipo.

  Nombre del ensamblado muestra el nombre del ensamblado .NET Framework que incluye el espacio de nombres para cada componente. Ordene esta columna para mostrar los espacios de nombres contenidos en cada ensamblado de .NET Framework instalado en el equipo.

  Directorio muestra la ubicación del ensamblado de .NET Framework. La ubicación predeterminada de todos los ensamblados es la caché global de ensamblados. Para obtener más información sobre la caché global de ensamblados, consulte [Trabajar con ensamblados y la caché global de ensamblados](https://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433).

## <a name="uielement-list"></a>Lista de UIElement
 **Filtro** de Filtra la lista de controles de WPF en función de la cadena que se proporciona en el cuadro de texto. Se muestran todas las coincidencias encontradas en cualquiera de las cuatro columnas.

 **Borrar** Borra la cadena de filtro.

 **Examinar** Abre el cuadro de diálogo **abrir** , que le permite desplazarse a los ensamblados que contienen controles WPF. Úselo para cargar ensamblados que no se encuentran en la caché global de ensamblados.

 **Idioma** de Muestra el idioma localizado del ensamblado que contiene el control WPF seleccionado.

## <a name="limitations"></a>Limitaciones
 Agregar un control personalizado o <xref:System.Windows.Controls.UserControl> al cuadro de herramientas tiene las limitaciones siguientes.

- Solo funciona con los controles personalizados definidos fuera del proyecto actual.

- No se actualiza correctamente al cambiar la configuración de soluciones de Depuración a Lanzamiento ni de Lanzamiento a Depuración. Esto se debe a que la referencia no es una referencia de proyecto, sino para el ensamblado en el disco. Si el control forma parte de la solución actual, al cambiar de Depuración a Lanzamiento, el proyecto sigue haciendo referencia a la versión de depuración del control.

  Además, si se aplican metadatos en tiempo de diseño al control personalizado y estos metadatos especifican que [ToolboxBrowsableAttribute](/previous-versions/visualstudio/visual-studio-2010/bb547991(v=vs.100)) está establecido en `false`, el control no aparece en el cuadro de herramientas.

  Puede hacer referencia a los controles directamente en la vista XAML mediante la asignación del espacio de nombres y el ensamblado para el control. Para obtener más información, consulte [Cómo: Importar un espacio de nombres a XAML](https://msdn.microsoft.com/6cda7c7a-369c-47dd-9c2d-13a35dcf737c).

## <a name="see-also"></a>Vea también

- [Elegir elementos del cuadro de herramientas (Cuadro de diálogo): Visual Studio](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
- [Cuadro de herramientas](../../ide/reference/toolbox.md)
- [Cómo: Usar un control de WPF de otro proveedor en una aplicación de WPF](https://msdn.microsoft.com/f4c0b601-3818-4f9f-85e5-77905f3b427f)
- [WPF Designer](https://msdn.microsoft.com/c6c65214-8411-4e16-b254-163ed4099c26)