---
title: "C&#243;mo: Asignar esquemas a documentos de Word en Visual Studio | Microsoft Docs"
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
  - "asignaciones [desarrollo de Office en Visual Studio], esquemas XML a documentos de Word"
  - "Word [desarrollo de Office en Visual Studio], asignar esquemas XML"
  - "esquemas XML [desarrollo de Office en Visual Studio], asignar"
ms.assetid: 9bfb3c7b-6392-45bd-b4c1-b2012b9ded69
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# C&#243;mo: Asignar esquemas a documentos de Word en Visual Studio
  La información de**Importante** The establecida en este tema relacionada con Microsoft Word se presenta exclusivamente para el marcado y el uso de individuos y organizaciones que se encuentran fuera de los Estados Unidos y sus territorios o que estén utilizando, o desarrollando programas que se ejecutan en, productos de Microsoft Word que se autorizados por Microsoft antes de enero de 2010, cuando Microsoft quitó una implementación de la funcionalidad concreta relacionada con XML personalizado de Microsoft Word.  Puede que esta información relacionada con Microsoft Word no sea leída o utilizada por individuos u organizaciones residentes en los Estados Unidos o sus territorios que estén utilizando, o desarrollando programas que se ejecutan en, productos de Microsoft Word con licencia concedida por Microsoft después del 10 de enero de 2010; dichos productos no tendrán el mismo comportamiento que los productos con licencia anterior a esa fecha o comprados, y con licencia para su uso, fuera de los Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Se puede asignar un esquema XML a un documento mientras el documento está abierto en un proyecto de Visual Studio.  Se utilizan las mismas herramientas de Microsoft Office Word que se utilizan cuando el documento está abierto fuera de Visual Studio.  El proyecto de Office crea los mismos objetos independientemente de si asigna el esquema al documento antes o después de crear la solución de Word.  
  
### Para asignar un esquema XML a un documento de Word en Visual Studio  
  
1.  Abra el documento o proyecto de plantilla de Word en Visual Studio.  
  
2.  Haga clic en el documento para desplazar el foco al diseñador.  
  
3.  En la cinta de opciones, haga clic en la ficha **Desarrollador**.  
  
    > [!NOTE]  
    >  Si la ficha **Desarrollador** no está visible, debe mostrarla primero.  Para obtener más información, vea [Cómo: Mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  En el grupo **XML**, haga clic en **Esquema**.  
  
     Se abrirá el cuadro de diálogo **Plantillas y complementos**.  
  
5.  Haga clic en la ficha **Esquema XML**.  
  
6.  Haga clic en **Agregar esquema**.  
  
     Se abre el cuadro de diálogo **Agregar esquema**.  
  
7.  Vaya a su archivo de esquema, selecciónelo y, a continuación, haga clic en **Abrir**.  
  
     Se abre el cuadro de diálogo **Configuración del esquema**.  
  
8.  Asigne un alias o haga clic en **Aceptar** para agregar el esquema sin un alias.  
  
9. Haga clic en **Aceptar**.  
  
     Se abre la ventana **Estructura XML**.  
  
10. Arrastre los elementos desde la ventana **Estructura XML** hasta los lugares de su documento donde desee crear los controles correspondientes.  
  
## Vea también  
 [Cómo: Asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Esquemas y datos XML en personalizaciones de nivel de documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  