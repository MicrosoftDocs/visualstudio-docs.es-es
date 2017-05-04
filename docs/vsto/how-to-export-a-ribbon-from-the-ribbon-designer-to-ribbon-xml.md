---
title: "C&#243;mo: Exportar una cinta de opciones del dise&#241;ador de la cinta de opciones a XML de la cinta de opciones | Microsoft Docs"
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
  - "Cinta de opciones personalizada, XML"
  - "personalizar la cinta de opciones, XML"
  - "exportar la cinta de opciones"
  - "Cinta [desarrollo de Office en Visual Studio], exportar"
  - "Cinta [desarrollo de Office en Visual Studio], XML"
  - "Diseñador de la cinta de opciones [desarrollo de Office en Visual Studio]"
  - "XML [desarrollo de Office en Visual Studio], cinta de opciones"
ms.assetid: 96e0e9ed-4392-4f45-ac33-b6f7c22ea321
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# C&#243;mo: Exportar una cinta de opciones del dise&#241;ador de la cinta de opciones a XML de la cinta de opciones
  El elemento **Cinta \(diseñador visual\)** no admite todos los tipos posibles de personalización de la cinta de opciones.  Para realizar personalizaciones avanzadas de la cinta de opciones, puede exportar la cinta desde el diseñador a un archivo XML de la cinta de opciones y editar el archivo XML directamente.  
  
> [!NOTE]  
>  En el archivo XML de la cinta de opciones no aparecen todos los valores de propiedades.  Para obtener más información, vea [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### Para exportar una cinta de opciones del diseñador de la cinta de opciones a XML de la cinta de opciones  
  
1.  Haga clic con el botón secundario en el archivo de código de la cinta de opciones del **Explorador de soluciones** y, a continuación, haga clic en **Ver diseñador**.  
  
2.  Haga clic con el botón secundario en el diseñador de la cinta de opciones y, a continuación, haga clic en **Exportar cinta de opciones a archivo XML**.  
  
     Visual Studio agrega al proyecto un archivo XML y un archivo de código XML, ambos de cinta de opciones.  
  
3.  En la clase de código Ribbon, busque los comentarios que empiezan por `TODO:.`  
  
4.  Copie el bloque de código de estos comentarios en la clase **ThisAddin**, **ThisWorkbook** o **ThisDocument**, dependiendo del tipo de solución que esté desarrollando.  
  
     Este código permite a la aplicación de Microsoft Office detectar y cargar la cinta de opciones personalizada.  Para obtener más información, vea [XML de la cinta de opciones](../vsto/ribbon-xml.md).  
  
5.  En la clase **ThisAddin**, **ThisWorkbook** o **ThisDocument**, quite las marcas de comentario del bloque de código.  
  
     Después de eliminar los comentarios del código, debe ser similar al ejemplo siguiente.  En este ejemplo, la clase Ribbon se denomina `MyRibbon`.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/ThisAddIn.vb#1)]  
  
6.  Cambie al archivo de código XML de la cinta de opciones y busque el área `Ribbon Callbacks`.  
  
     Aquí es donde se escriben los métodos de devolución de llamada para controlar las acciones del usuario, como hacer clic en un botón.  
  
7.  Cree un método de devolución de llamada para cada controlador de eventos escrito en el código del diseñador de la cinta de opciones.  
  
8.  Mueva todo el código controlador de eventos de los controladores de eventos a los métodos de devolución de llamada y modifique el código para que funcione con el modelo de programación de extensibilidad de la cinta de opciones \(RibbonX\).  
  
     Para obtener información sobre cómo escribir métodos de devolución de llamada y utilizar el modelo de programación RibbonX, vea [XML de la cinta de opciones](../vsto/ribbon-xml.md).  
  
## Vea también  
 [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)   
 [Diseñador de la cinta de opciones](../vsto/ribbon-designer.md)   
 [XML de la cinta de opciones](../vsto/ribbon-xml.md)   
 [Tutorial: Crear una pestaña personalizada usando el diseñador de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Tutorial: Crear una pestaña personalizada usando XML de la cinta de opciones](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  