---
title: "C&#243;mo: Agregar comandos a men&#250;s contextuales"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "menús de Office, crear"
  - "[desarrollo de Office en Visual Studio], menús contextuales"
ms.assetid: 9a848817-db11-4294-8f6f-9181ab87aadd
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# C&#243;mo: Agregar comandos a men&#250;s contextuales
  En este tema se muestra cómo agregar comandos a un menú contextual en una aplicación de Office mediante un complemento de VSTO.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
### Para agregar comandos a los menús contextuales de Office  
  
1.  Agregue un elemento **XML de cinta** a un proyecto de nivel de documento o de complemento de VSTO. Para obtener más información, consulte [Cómo: Iniciarse en la personalización de la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md). En  
  
2.  el **Explorador de soluciones**, seleccione **ThisAddIn.cs** o **ThisAddIn.vb**.  
  
3.  En la barra de menús, elija **Ver**, **Código**.  
  
     El archivo de clase **ThisAddin** se abrirá en el Editor de código.  
  
4.  Agregue el siguiente código a la clase **ThisAddin**. Este código invalida el método CreateRibbonExtensibilityObject y devuelve la clase XML Ribbon a la aplicación de Office.  
  
     [!code-csharp[Trin_WordAddIn_Menus#1](../snippets/csharp/VS_Snippets_OfficeSP/trin_wordaddin_menus/cs/thisaddin.cs#1)]
     [!code-vb[Trin_WordAddIn_Menus#1](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_wordaddin_menus/vb/thisaddin.vb#1)]  
  
5.  En el **Explorador de soluciones**, seleccione el archivo XML de cinta. De forma predeterminada, el archivo XML de cinta se denomina Ribbon1.xml.  
  
6.  En la barra de menús, elija **Ver**, **Código**.  
  
     Se abrirá el archivo de código XML de cinta de opciones en el Editor de código.  
  
7.  En el Editor de código, agregue el código XML que describe el menú contextual y el control que quiere agregar al menú contextual.  
  
     En el ejemplo siguiente se agrega un botón, un menú y un control de galería al menú contextual de un documento de Word. El id. del control de este menú contextual es ContextMenuText. Para obtener una lista completa de identificadores de control de acceso directo de Office 2010, consulte [Archivos de ayuda de Office 2010: identificadores de control de la interfaz de usuario de Office Fluent](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui"> <contextMenus> <contextMenu idMso="ContextMenuText"> <button id="MyButton" label="My Button" insertBeforeMso="HyperlinkInsert" onAction="GetButtonID" /> <menu id="MySubMenu" label="My Submenu" > <button id="MyButton2" label="Button on submenu" /> </menu> <gallery id="galleryOne" label="My Gallery"> <item id="item1" imageMso="HappyFace" /> <item id="item2" imageMso="HappyFace" /> <item id="item3" imageMso="HappyFace" /> <item id="item4" imageMso="HappyFace" /> </gallery> </contextMenu> </contextMenus> </customUI>  
    ```  
  
8.  En el **Explorador de soluciones**, elija **MyRibbon.cs** o **MyRibbon.vb**.  
  
9. Agregue un método de devolución de llamada a la clase `Ribbon1` para cada control que quiere administrar.  
  
     El siguiente método de devolución de llamada controla el botón **Mi botón**. Este código agrega una cadena al documento activo en la posición actual del cursor.  
  
     [!code-csharp[Trin_WordAddIn_Menus#2](../snippets/csharp/VS_Snippets_OfficeSP/trin_wordaddin_menus/cs/ribbon1.cs#2)]
     [!code-vb[Trin_WordAddIn_Menus#2](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_wordaddin_menus/vb/ribbon1.vb#2)]  
  
## Vea también  
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Tutorial: Crear menús de acceso directo para marcadores](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Personalizar menús contextuales de Office 2010](http://go.microsoft.com/fwlink/?LinkId=182186)  
  
  