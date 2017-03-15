---
title: Elegir elementos del cuadro de herramientas, Componentes de WPF | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 8d34a09ec4716a9ab2d5fbaea6c93657961c1c43
ms.lasthandoff: 02/22/2017

---
# <a name="choose-toolbox-items-wpf-components"></a>Elegir elementos del cuadro de herramientas, Componentes de WPF
En esta pestaña del cuadro de diálogo **Elegir elementos del cuadro de herramientas**, se muestra una lista de controles de Windows Presentation Foundation (WPF) disponibles en el equipo local. Para mostrar esta lista, seleccione **Elegir elementos del cuadro de herramientas** del menú **Herramientas** para mostrar el cuadro de diálogo **Elegir elementos del cuadro de herramientas** y después seleccione la pestaña **Componentes WPF**. Para ordenar los componentes de la lista, seleccione cualquier encabezado de columna.  
  
-   Cuando se seleccione la casilla junto a un componente, se mostrará un icono de ese componente en el **cuadro de herramientas**.  
  
    > [!TIP]
    >  Para agregar una instancia de un control de WPF a un documento del proyecto abierto para su edición, arrastre su icono de **cuadro de herramientas** a la superficie de la vista Diseño. El marcado y el código predeterminados del componente se insertan en el proyecto, preparados para que los pueda modificar. Para obtener más información, consulte [Cómo: Administrar la ventana Cuadro de herramientas](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2) y [Cómo: Manipular fichas del cuadro de herramientas](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
-   Cuando se desactive la casilla junto a un componente, el icono correspondiente se quitará del **cuadro de herramientas.**  
  
    > [!NOTE]
    >  Los componentes de .NET Framework instalados en el equipo siguen estando disponibles aunque no se muestren sus iconos en el **cuadro de herramientas**.  
  
 Las columnas de la pestaña **Componentes WPF** contienen la siguiente información:  
  
 Nombre  
 Enumera los nombres de los controles de WPF para los que existen entradas en el Registro del equipo.  
  
 Espacio de nombres  
 Muestra la jerarquía del espacio de nombres de la [biblioteca de clases .NET Framework](http://msdn.microsoft.com/en-us/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29) que define la estructura del componente. Ordene esta columna para mostrar los componentes disponibles en cada espacio de nombres de .NET Framework instalado en el equipo.  
  
 Nombre del ensamblado  
 Muestra el nombre del ensamblado de .NET Framework que incluye el espacio de nombres de cada componente. Ordene esta columna para mostrar los espacios de nombres contenidos en cada ensamblado de .NET Framework instalado en el equipo.  
  
 Directorio  
 Muestra la ubicación del ensamblado de .NET Framework. La ubicación predeterminada de todos los ensamblados es la caché global de ensamblados. Para obtener más información sobre la caché global de ensamblados, consulte [Trabajar con ensamblados y la caché global de ensamblados](http://msdn.microsoft.com/Library/8a18e5c2-d41d-49ef-abcb-7c27e2469433).  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Filtrar**  
 Filtra la lista de controles de WPF según la cadena proporcionada en el cuadro de texto. Se muestran todas las coincidencias encontradas en cualquiera de las cuatro columnas.  
  
 **Borrar**  
 Borra la cadena de filtro.  
  
 **Examinar**  
 Abre el cuadro de diálogo **Abrir**, que le permite ir a ensamblados que contienen controles de WPF. Úselo para cargar ensamblados que no se encuentran en la caché global de ensamblados.  
  
 **Idioma**  
 Muestra el lenguaje localizado del ensamblado que contiene el control de WPF seleccionado.  
  
## <a name="limitations"></a>Limitaciones  
 Agregar un control personalizado o <xref:System.Windows.Controls.UserControl> al cuadro de herramientas tiene las siguientes limitaciones.  
  
-   Solo funciona con los controles personalizados definidos fuera del proyecto actual.  
  
-   No se actualiza correctamente al cambiar la configuración de soluciones de Depuración a Lanzamiento ni de Lanzamiento a Depuración. Esto se debe a que la referencia no es una referencia de proyecto, sino para el ensamblado en el disco. Si el control forma parte de la solución actual, al cambiar de Depuración a Lanzamiento, el proyecto sigue haciendo referencia a la versión de depuración del control.  
  
 Además, si se aplican metadatos en tiempo de diseño al control personalizado y estos especifican que el atributo <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> se establece en `false`, el control no aparece en el cuadro de herramientas.  
  
 Puede hacer referencia a los controles directamente en la vista XAML mediante la asignación del espacio de nombres y el ensamblado para el control. Para obtener más información, consulte [Cómo: Importar un espacio de nombres a XAML](http://msdn.microsoft.com/en-us/6cda7c7a-369c-47dd-9c2d-13a35dcf737c).  
  
## <a name="see-also"></a>Vea también  
 [Elegir elementos del cuadro de herramientas (Cuadro de diálogo): Visual Studio](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [Cuadro de herramientas](../../ide/reference/toolbox.md)   
 [Cómo: Usar un control de WPF de otro proveedor en una aplicación de WPF](http://msdn.microsoft.com/en-us/f4c0b601-3818-4f9f-85e5-77905f3b427f)   
 [WPF Designer](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
