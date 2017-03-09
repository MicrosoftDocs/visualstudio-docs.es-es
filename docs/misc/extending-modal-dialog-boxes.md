---
title: "Extender cuadros de di&#225;logo modales | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "cuadros de diálogo modales en extensiones de Visual Studio"
  - "extensiones de Visual Studio, cuadros de diálogo modales"
ms.assetid: 478743dc-9fd9-46d7-9739-859fb8841a4f
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# Extender cuadros de di&#225;logo modales
Para garantizar la compatibilidad funcional y visual con Visual Studio, cree cuadros de diálogo modales para extensiones de Visual Studio derivando las ventanas del cuadro de diálogo del objeto <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>. Los cuadros de diálogo derivados de esta manera también pueden proporcionar funciones adicionales; por ejemplo, puede establecer destinos de la F1 Ayuda y permitir minimizar y maximizar en la ventana.  
  
## Crear cuadros de diálogo modales  
  
1.  En el proyecto, agregue una referencia a System.XAML.  
  
2.  En el **Explorador de soluciones**, haga clic con el botón secundario en el proyecto, haga clic en **Agregar** y, a continuación, en **Ventana**.  
  
3.  Asigne un nombre a la ventana y haga clic en **Agregar**.  
  
     Aparece una ventana XAML vacía en el diseñador.  
  
4.  En el elemento `Window` de nivel superior, agregue una declaración de espacio de nombres para <xref:Microsoft.VisualStudio.PlatformUI>, y cambie el elemento `Window` por un elemento <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, tal como se muestra en el ejemplo siguiente.  
  
     [!code-xml[VSModalDialog#02](../misc/codesnippet/Xaml/extending-modal-dialog-boxes_1.xaml)]  
  
5.  Agregue botones, etiquetas y otros controles del **Cuadro de herramientas**, escriba las etiquetas de texto y ajuste la apariencia del cuadro de diálogo.  
  
6.  Cambie a la vista de código.  
  
7.  En la definición de clase, establezca la clase para que herede de <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>. \(De forma predeterminada, la clase hereda de <xref:System.Windows.Window?displayProperty=fullName>\).  
  
8.  Agregue controladores de eventos para botones y otros controles.  
  
#### Para agregar F1 Ayuda para un cuadro de diálogo modal  
  
1.  Para el constructor, agregue un parámetro que tome una cadena como argumento y establezca el constructor para que herede del constructor base con el mismo parámetro, tal como se muestra en el ejemplo siguiente.  
  
     [!code-cs[VSModalDialog#12](../misc/codesnippet/CSharp/extending-modal-dialog-boxes_2.cs)]  
  
     Este constructor establece la propiedad <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasHelpButton%2A> en `true` y permite usar la cadena recibida como palabra clave cuando un usuario presiona la tecla F1 o hace clic en el botón **Ayuda**.  
  
#### Para agregar botones Minimizar y Maximizar a un cuadro de diálogo modal  
  
1.  En la función de constructor, establezca las propiedades <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.hasMinimizeButton%2A> y <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.hasHMaximizeButton%2A> en `true`, como se muestra en el ejemplo siguiente.  
  
     [!code-cs[VSModalDialog#13](../misc/codesnippet/CSharp/extending-modal-dialog-boxes_3.cs)]  
  
    > [!WARNING]
    >  Cuando se muestran los botones **Minimizar** y **Maximizar**, el botón **Ayuda** se oculta, incluso si la propiedad <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasHelpButton%2A> está establecida en `true`.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra un cuadro de diálogo modal que tiene dos constructores. El primer constructor toma una palabra clave F1 como argumento y muestra un botón **Ayuda**. El segundo constructor no toma ningún argumento, pero muestra los botones **Minimizar** y **Maximizar**. Al hacer clic en el botón **Sí**, se invoca una segunda instancia del cuadro de diálogo y se habilita la Ayuda.  
  
 [!code-xml[VSModalDialog#01](../misc/codesnippet/Xaml/extending-modal-dialog-boxes_4.xaml)]  
  
 [!code-cs[VSModalDialog#11](../misc/codesnippet/CSharp/extending-modal-dialog-boxes_5.cs)]  
  
 El código siguiente invoca el cuadro de diálogo desde un controlador de eventos.  
  
 [!code-cs[VSModalDialog#21](../misc/codesnippet/CSharp/extending-modal-dialog-boxes_6.cs)]  
  
## Vea también  
 [Creación y administración de cuadros de diálogo modales](../extensibility/creating-and-managing-modal-dialog-boxes.md)