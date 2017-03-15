---
title: "Arquitectura de la p&#225;gina de inicio | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "arquitectura de la página de inicio"
  - "xaml de la página de inicio"
ms.assetid: f94afe27-0be3-47d9-8e17-b0fd429017bd
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Arquitectura de la p&#225;gina de inicio
Este documento describe la arquitectura de la ventana de herramientas de la página principal que se incluye en Visual Studio.  Puede utilizar esta información para agregar o cambiar elementos en la página de inicio sin cambiar su estructura subyacente.  
  
 La página principal de Visual Studio se escribe en el \(WPF\) lenguaje de marcado de aplicaciones Extensible de Windows Presentation Foundation \(XAML\).  Para obtener más información sobre el marcado XAML, vea [Información general sobre XAML \(WPF\)](../Topic/XAML%20Overview%20\(WPF\).md).  
  
## estructura de la página  
 La página de inicio está compuesto por un elemento de <xref:System.Windows.Controls.Image> y dos elementos de <xref:System.Windows.Controls.Grid> en un elemento de `Grid`de nivel superior.  el elemento de `Image` abarca la parte superior de la ventana de herramientas y contiene el logotipo de Visual Studio.  Debajo del logotipo, el elemento de `Grid`de la izquierda contiene botones de comando para los nuevos proyectos, la lista de **Proyectos recientes** , y un área para las opciones de página principal.  El elemento de `Grid`de la derecha contiene un elemento de <xref:System.Windows.Controls.TabControl> que tiene una pestaña de **Comenzar** , una ficha de **Información orientativa y recursos** , y una ficha de **Últimas noticias** .  Una columna central es definidas entre los elementos izquierdo y derecho de `Grid`, pero no tiene contenido y solo se utiliza como separación.  
  
### cuerpo de la ventana  
 El fondo de la ventana de herramientas está representado por el elemento de nivel superior de `Grid`.  Los anchos de las columnas principales son definidas aquí, en el elemento de `ColumnDefinitions` .  El alto de la imagen del logotipo se establece en el elemento de `RowDefinitions` .  
  
 Las definiciones y las definiciones de columna de la fila se almacenan en matrices de base cero.  Para colocar un elemento en una cuadrícula, establezca los atributos de `Grid.Column` y de `Grid.Row` para coincidir con los índices de <xref:System.Windows.Controls.ColumnDefinition> y los elementos correspondientes de <xref:System.Windows.Controls.RowDefinition> .  
  
### Imagen del logotipo  
 El logotipo de Visual Studio ocupa la fila superior de la cuadrícula de nivel superior \(`Grid.Row="0"`\) como un elemento de `Image` .  Para mostrar otra imagen, seleccione el atributo de `Source` de elemento de `Image` a otro archivo de imagen.  Para quitar la imagen, elimine el elemento de `Image` y establezca el atributo de `height` del elemento de nivel superior correspondiente de `RowDefinition` a `0` \(cero\) para ocultar la fila superior de la cuadrícula.  
  
### columna izquierda  
 La columna izquierda de la página de inicio está representada por un elemento de `Grid`en `Grid.Column="0"` y `Grid.Row="1"`.  Este elemento contiene definiciones para que tres filas, que el host la cuadrícula de los botones de comando, el Recientes proyectos la cuadrícula, y un elemento de `StackPanel` muestran las opciones de Visual Studio.  
  
 Puede agregar un elemento a esta cuadrícula agregándolo a una de las filas existentes o agregando una nueva definición de fila.  Cuando se define una nueva fila, recuerde aumentar los valores de `Grid.Row` de cualquier elemento que aparece en la nueva fila.  
  
### La columna central  
 La columna central es un separación y no contiene ningún elemento.  Para agregar un elemento a la columna, a colóquelo en `Grid.Column="1"` y a `Grid.Row="1"`multimedia.  Asegúrese de incluir el atributo de `Width` de la definición de columna para alojar el cambio.  
  
### columna derecha  
 la columna derecha contiene un elemento de `Grid` en `Grid.Column="1"` y `Grid.Row="1"`.  La cuadrícula contiene un elemento de `TabControl` que tiene tres fichas.  
  
 Puede agregar una pestaña agregando un elemento de <xref:System.Windows.Controls.TabItem> al control de ficha, como se muestra en [Tutorial: Agregar XAML personalizado a la página de inicio](../extensibility/walkthrough-adding-custom-xaml-to-the-start-page.md), o puede modificar o quitar las tabulaciones existentes.  Las fichas aparecen de izquierda a derecha en la interfaz \(UI\) de usuario en el mismo orden en que aparecen de arriba abajo en el marcado.  
  
 Si agrega un elemento a la cuadrícula de la columna derecha fuera del control de ficha, se recomienda definir una nueva fila o columna de la cuadrícula para asegurarse de que aparece como esperada.  
  
## Vea también  
 [Personalizar la página principal](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Procedimientos recomendados de la página de inicio](../misc/start-page-best-practices.md)   
 [Implementar páginas de inicio personalizado](../extensibility/deploying-custom-start-pages.md)