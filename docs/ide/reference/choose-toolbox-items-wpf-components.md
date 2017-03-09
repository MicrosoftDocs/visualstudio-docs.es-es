---
title: "Elegir elementos del cuadro de herramientas, Componentes de WPF | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.chooseitems.wpfcomponents"
helpviewer_keywords: 
  - "Pestaña Componentes de WPF, cuadro de diálogo Elegir elementos del cuadro de herramientas"
  - "cuadro de diálogo Elegir elementos del cuadro de herramientas, pestaña Componentes de WPF"
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Elegir elementos del cuadro de herramientas, Componentes de WPF
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta ficha del cuadro de diálogo **Elegir elementos del cuadro de herramientas** muestra una lista de los controles de Windows Presentation Foundation \(WPF\) disponibles en el equipo local.  Para mostrar esta lista, seleccione la opción **Elegir elementos del cuadro de herramientas** del menú **Herramientas** con el fin de mostrar el cuadro de diálogo **Elegir elementos del cuadro de herramientas** y, a continuación, seleccione la ficha **Componentes WPF**.  Para ordenar los componentes de la lista, seleccione cualquier encabezado de columna.  
  
-   Cuando la casilla situada junto a un componente esté activada, se mostrará un icono de ese componente en el **Cuadro de herramientas**.  
  
    > [!TIP]
    >  Para agregar una instancia de un control de WPF a un documento del proyecto abierto para su edición, arrastre el icono del **Cuadro de herramientas** a la superficie de la vista Diseño.  El código y marcado predeterminados del componente se insertan en el proyecto, preparado para que pueda modificarlo.  Para obtener más información, vea [How to: Manage the Toolbox Window](http://msdn.microsoft.com/es-es/a022c3fe-298c-4a59-a48f-b050da90ebc2) y [How to: Manipulate Toolbox Tabs](http://msdn.microsoft.com/es-es/21285050-cadd-455a-b1f5-a2289a89c4db).  
  
-   Cuando se desactiva la casilla situada al lado de un componente, el icono correspondiente se quita del **Cuadro de herramientas.**  
  
    > [!NOTE]
    >  Los componentes de .NET Framework instalados en su equipo permanecen disponibles independientemente de que se muestren o no en el **Cuadro de herramientas**.  
  
 Las columnas de la ficha **Componentes WPF** contienen la siguiente información:  
  
 Name  
 Muestra los nombres de los controles de WPF para los que existen entradas en el Registro del equipo.  
  
 Espacio de nombres  
 Muestra la jerarquía del espacio de nombres de [NIB: .NET Framework Class Library](http://msdn.microsoft.com/es-es/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29) que define la estructura del componente.  Ordene esta columna para mostrar los componentes disponibles dentro de cada espacio de nombres de .NET Framework instalado en el equipo.  
  
 Nombre del ensamblado  
 Muestra el nombre del ensamblado de .NET Framework que incluye el espacio de nombres de cada componente.  Ordene esta columna para que muestre los espacios de nombres contenidos en cada ensamblado de .NET Framework instalado en el equipo.  
  
 Directorio  
 Muestra la ubicación del ensamblado de .NET Framework.  La ubicación predeterminada de todos los ensamblados es la Caché global de ensamblados.  Para obtener información adicional sobre la memoria caché global de ensamblados, vea [Trabajar con ensamblados y la memoria caché global de ensamblados](../Topic/Working%20with%20Assemblies%20and%20the%20Global%20Assembly%20Cache.md).  
  
## Lista de UIElement  
 **Filtro**  
 Filtra la lista de controles de WPF basándose en la cadena que se proporcione en el cuadro de texto.  Se muestran todas las coincidencias de cualquiera de las cuatro columnas.  
  
 **Clear**  
 Borra la cadena de filtro.  
  
 **Browse**  
 Abre el cuadro de diálogo **Abrir**, que permite navegar a ensamblados que contienen controles de WPF.  Utilice esta opción para cargar ensamblados que no se encuentran en la Caché global de ensamblados.  
  
 **Language**  
 Muestra el lenguaje adaptado del ensamblado que contiene el control de WPF seleccionado.  
  
## Limitaciones  
 Agregar un control personalizado o <xref:System.Windows.Controls.UserControl> al Cuadro de herramientas tiene las limitaciones siguientes.  
  
-   Sólo funciona para los controles personalizados definidos fuera del proyecto actual.  
  
-   No se actualiza correctamente al cambiar la configuración de la solución del modo depuración al modo lanzamiento, o viceversa.  Esto se debe a que la referencia no es una referencia de proyecto, sino que corresponde al ensamblado del disco.  Si el control forma parte de la solución actual, al cambiar del modo depuración al modo lanzamiento, el proyecto continúa haciendo referencia a la versión de depuración del control.  
  
 Además, si se aplican metadatos en tiempo de diseño al control personalizado y estos metadatos especifican que <xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> está establecido en `false`, el control no aparece en el Cuadro de herramientas.  
  
 Puede hacer referencia directamente a los controles en la vista XAML asignando el espacio de nombres y el ensamblado para el control.  Para obtener más información, vea [Cómo: Importar un espacio de nombres a XAML](http://msdn.microsoft.com/es-es/6cda7c7a-369c-47dd-9c2d-13a35dcf737c).  
  
## Vea también  
 [Choose Toolbox Items Dialog Box \(Visual Studio\)](http://msdn.microsoft.com/es-es/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [cuadro de herramientas](../../ide/reference/toolbox.md)   
 [Cómo: Usar un control de WPF de otro proveedor en una aplicación de WPF](http://msdn.microsoft.com/es-es/f4c0b601-3818-4f9f-85e5-77905f3b427f)   
 [WPF Designer](http://msdn.microsoft.com/es-es/c6c65214-8411-4e16-b254-163ed4099c26)