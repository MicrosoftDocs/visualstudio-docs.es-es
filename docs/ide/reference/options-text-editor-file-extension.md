---
title: "Opciones, editor de texto, extensión de archivo | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.toolsoptionspages.text_editor.file_extension
helpviewer_keywords:
- file extensions, associating to editor
- Editing Experience
- Options dialog box
- Editing Experience, selecting
ms.assetid: 05298fc5-fc4e-4bb2-b942-1f7d2dcdff0f
caps.latest.revision: 12
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 37e5b813482eae6c4d46051ed4b261594d9e5164
ms.contentlocale: es-es
ms.lasthandoff: 05/24/2017

---
# <a name="options-text-editor-file-extension"></a>Opciones, editor de texto, extensión de archivo
Este cuadro de diálogo Opciones le permite especificar cómo se controlarán todos los archivos con determinadas extensiones de archivo mediante el Entorno de desarrollo integrado (IDE) de Visual Studio. Para cada **extensión** que especifique, puede seleccionar un editor asociado. Esto le permite elegir el diseñador o el editor del IDE en el que se abrirán los documentos de un tipo determinado. Para mostrar estas opciones, pulse **Opciones** del menú **Herramientas**, expanda el nodo **Editor de texto** y seleccione **Extensión de archivo**.  
  
 Cuando selecciona una opción "con codificación", se mostrará un cuadro de diálogo siempre que abra un documento de ese tipo que le permite seleccionar un esquema de codificación para ese documento. Esto puede resultar útil si está preparando versiones de sus documentos de proyecto para usarlos en diferentes plataformas o en diferentes idiomas de destino.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Extensión**  
 Escriba la extensión de archivo cuyo editor asociado en el IDE quiere definir.  
  
 **Editor**  
 Seleccione el diseñador o el editor del IDE en el que se abrirán los documentos con esta extensión de archivo. Cuando selecciona una opción "con codificación", se mostrará un cuadro de diálogo siempre que abra dicho documento que le permite seleccionar un esquema de codificación.  
  
 **Add**  
 Agrega una entrada que incluye la **extensión** y el **editor asociado** especificados a la lista de extensiones.  
  
 **Remove**  
 Elimina la entrada seleccionada de la lista de extensiones.  
  
 Lista de extensiones  
 Muestra todas las extensiones para las que se ha especificado un editor asociado.  
  
 **Asignar archivos sin extensión**  
 Seleccione esta opción si quiere especificar cómo se controlarán los archivos sin una extensión mediante el IDE.  
  
 **Opciones de archivos sin extensión**  
 Proporciona la misma lista que el **Editor**. Seleccione el diseñador o el editor del IDE en el que se abrirán los documentos sin extensiones de archivo.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Administrar los modos del editor](../../ide/how-to-manage-editor-modes.md)
