---
title: "Opciones, editor de texto, extensi&#243;n de archivo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.toolsoptionspages.text_editor.file_extension"
helpviewer_keywords: 
  - "extensiones de archivo, asociar al editor"
  - "Editor asociado"
  - "Opciones (cuadro de diálogo)"
  - "Editor asociado, seleccionar"
ms.assetid: 05298fc5-fc4e-4bb2-b942-1f7d2dcdff0f
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Opciones, editor de texto, extensi&#243;n de archivo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El cuadro de diálogo Opciones permite especificar cómo controlará el entorno de desarrollo integrado \(IDE\) de Visual Studio todos los archivos con determinadas extensiones de archivo.  Para cada **extensión** que se escribe es posible seleccionar un editor asociado.  Esto permite elegir el diseñador o editor de IDE en que se abrirá un determinado tipo de documentos.  Para mostrar estas opciones, elija **Opciones** en el menú **Herramientas**, expanda el nodo **Editor de texto** y seleccione **Extensión de archivo**.  
  
 Al seleccionar una opción "con codificación", se mostrará un cuadro de diálogo, siempre que abra un documento de dicho tipo, en el que seleccionar un esquema de codificación para el documento.  Esto puede ser útil si está preparando versiones de los documentos del proyecto para que se utilicen en diversas plataformas o diferentes lenguajes de destino.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos.  Para cambiar la configuración, elija **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Lista de UIElement  
 **Extensión**  
 Escriba la extensión de archivo cuyo editor asociado en el IDE desea definir.  
  
 **Editor**  
 Seleccione el diseñador o editor de IDE en el que se abrirán los documentos con esta extensión de archivo.  Al seleccionar una opción "con codificación" se mostrará un cuadro de diálogo siempre que abra ese documento, en el que seleccionar un esquema de codificación.  
  
 **Agregar**  
 Agrega una entrada que incluye la **extensión** especificada y el **Editor asociado** a la lista de extensiones.  
  
 **Remove**  
 Elimina la entrada seleccionada de la lista de extensiones.  
  
 Lista de extensiones  
 Muestra todas las extensiones para las que se ha especificado un editor asociado.  
  
 **Asignar archivos sin extensión**  
 Seleccione esta opción si desea especificar la forma en que el IDE controlará los archivos sin extensión.  
  
 **Opciones de archivos sin extensión**  
 Proporciona la misma lista que la opción **Editor**.  Seleccione el diseñador o editor de IDE en que se abrirán los documentos sin extensiones de archivo.  
  
## Vea también  
 [Cómo: Administrar los modos del editor](../../ide/how-to-manage-editor-modes.md)