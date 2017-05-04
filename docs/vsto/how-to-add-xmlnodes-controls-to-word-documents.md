---
title: "C&#243;mo: Agregar controles XMLNodes a documentos de Word | Microsoft Docs"
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
  - "controles [desarrollo de Office en Visual Studio], agregar a documentos"
  - "XMLNodes (control), agregar a documentos"
ms.assetid: 315c6def-51f6-4ba6-bd9e-55cdf70f15bf
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# C&#243;mo: Agregar controles XMLNodes a documentos de Word
  La información de**Importante** The establecida en este tema relacionada con Microsoft Word se presenta exclusivamente para el marcado y el uso de individuos y organizaciones que se encuentran fuera de los Estados Unidos y sus territorios o que estén utilizando, o desarrollando programas que se ejecutan en, productos de Microsoft Word que se autorizados por Microsoft antes de enero de 2010, cuando Microsoft quitó una implementación de la funcionalidad concreta relacionada con XML personalizado de Microsoft Word.  Puede que esta información relacionada con Microsoft Word no sea leída o utilizada por individuos u organizaciones residentes en los Estados Unidos o sus territorios que estén utilizando, o desarrollando programas que se ejecutan en, productos de Microsoft Word con licencia concedida por Microsoft después del 10 de enero de 2010; dichos productos no tendrán el mismo comportamiento que los productos con licencia anterior a esa fecha o comprados, y con licencia para su uso, fuera de los Estados Unidos.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Cuando se asigna un elemento de esquema XML repetitivo a un documento de Microsoft Office Word, Visual Studio agrega automáticamente un control <xref:Microsoft.Office.Tools.Word.XMLNodes> al documento.  
  
 Para obtener información sobre cómo asignar los elementos de esquema XML que no son de repetición, vea [Cómo: Agregar controles XMLNode a documentos de Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
> [!NOTE]  
>  El control <xref:Microsoft.Office.Tools.Word.XMLNodes> no está disponible en el **Cuadro de herramientas** ni en la ventana **Orígenes de datos**, ni se puede crear mediante programación.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Para agregar un control XMLNodes a un documento  
  
1.  En el documento hospedado en el diseñador de Visual Studio, en la Cinta de opciones, haga clic en la pestaña **Desarrollador**.  
  
    > [!NOTE]  
    >  Si la ficha **Desarrollador** no está visible, debe mostrarla primero.  Para obtener más información, vea [Cómo: Mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
2.  En el grupo **XML**, haga clic en **Esquema**.  
  
     Se abrirá el cuadro de diálogo **Plantillas y complementos**.  
  
3.  Haga clic en la ficha **Esquema XML**.  
  
4.  Haga clic en **Agregar esquema**.  
  
     Se abre el cuadro de diálogo **Agregar esquema**.  
  
5.  Seleccione un esquema XML que contenga elementos de esquema repetitivos y haga clic en **Abrir**.  
  
     Aparece el cuadro de diálogo **Configuración del esquema**.  
  
6.  Asigne un alias o haga clic en **Aceptar** para agregar el esquema sin un alias.  
  
     El esquema se agrega al cuadro de diálogo **Agregar esquema**.  
  
7.  En el cuadro de diálogo **Agregar esquema**, haga clic en **Aceptar**.  
  
     Se abre el panel de tareas **Estructura XML**.  
  
8.  Haga clic en el elemento de esquema de repetición en el panel de tareas **Estructura XML** para agregarlo al documento.  
  
     Se crea un control <xref:Microsoft.Office.Tools.Word.XMLNodes> y se agrega al proyecto.  
  
## Vea también  
 [XMLNodes &#40;Control&#41;](../vsto/xmlnodes-control.md)   
 [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  