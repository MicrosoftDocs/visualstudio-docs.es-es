---
title: Página Eventos de compilación, Diseñador de proyectos (C#) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5a73978bf78c26914e7ee6b21c27f1eb2e7682ea
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223103"
---
# <a name="build-events-page-project-designer-c"></a>Eventos de compilación (Página, Diseñador de proyectos) (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Use la página **Eventos de compilación** del **Diseñador de proyectos** para especificar las instrucciones de configuración de compilación. También puede especificar las condiciones en las que se ejecutan los eventos posteriores a la compilación. Para obtener más información, vea [Cómo: Especificar eventos de compilación (C#)](../../ide/how-to-specify-build-events-csharp.md) y [Cómo: Especificar eventos de compilación (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Configuración**  
 Este control no se puede modificar en esta página. Para obtener una descripción de este control, vea [Página Compilar Diseñador de proyectos (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Plataforma**  
 Este control no se puede modificar en esta página. Para obtener una descripción de este control, vea [Página Compilar Diseñador de proyectos (C#)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Línea de comandos del evento anterior a la compilación**  
 Especifica los comandos que se van a ejecutar antes de que empiece la compilación. Para escribir comandos largos, haga clic en **Edición anterior a la compilación** para mostrar el cuadro de diálogo [Línea de comandos del evento anterior a la compilación/Línea de comandos del evento posterior a la compilación](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
> [!NOTE]
>  Los eventos anteriores a la compilación no se ejecutan si el proyecto está actualizado y no se desencadena ninguna compilación.  
  
 **Línea de comandos del evento posterior a la compilación**  
 Especifica los comandos que se van a ejecutar después de que finalice la compilación. Para escribir comandos largos, haga clic en **Edición posterior a la compilación** para mostrar el cuadro de diálogo **Línea de comandos del evento anterior a la compilación/Línea de comandos del evento posterior a la compilación**.  
  
> [!NOTE]
>  Agregue una instrucción `call` antes de todos los comandos posteriores a la compilación que ejecutan archivos .bat. Por ejemplo: `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Ejecutar el evento posterior a la compilación**  
 Especifica las condiciones siguientes para que se ejecute el evento posterior a la compilación, como se muestra en la tabla siguiente.  
  
|Opción|Resultado|  
|------------|------------|  
|**Siempre**|El evento posterior a la compilación se ejecuta independientemente de si la compilación se realiza correctamente.|  
|**Si la compilación es correcta**|El evento posterior a la compilación se ejecuta si la compilación se realiza correctamente. Por lo tanto, el evento se ejecutará incluso para un proyecto actualizado, siempre y cuando la compilación se realice correctamente.|  
|**Cuando la compilación actualiza la salida del proyecto**|El evento posterior a la compilación solo se ejecuta si el archivo de salida del compilador (.exe o .dll) es diferente del anterior archivo de salida del compilador. Por lo tanto, un evento posterior a la compilación no se ejecuta si un proyecto está actualizado.|  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Especificar eventos de compilación (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Cómo: Especificar eventos de compilación (C#)](../../ide/how-to-specify-build-events-csharp.md)   
 [Referencia de propiedades del proyecto](../../ide/reference/project-properties-reference.md)   
 [Compilar y generar en Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)



