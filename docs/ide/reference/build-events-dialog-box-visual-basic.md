---
title: "Eventos de compilaci&#243;n (Cuadro de di&#225;logo) (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesBuildEvents"
helpviewer_keywords: 
  - "eventos de compilación"
  - "eventos de compilación, especificar"
  - "eventos anteriores a la compilación"
  - "Cuadro de diálogo Eventos de compilación"
  - "eventos posteriores a la compilación"
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# Eventos de compilaci&#243;n (Cuadro de di&#225;logo) (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilice el cuadro de diálogo **Eventos de compilación** para especificar las instrucciones de configuración de compilación.  También puede especificar las condiciones en las que se ejecutan los eventos anteriores y posteriores a la compilación.  Para obtener más información, vea [Cómo: Especificar eventos de compilación \(Visual Basic\)](../../ide/how-to-specify-build-events-visual-basic.md).  
  
 **Línea de comandos del evento anterior a la compilación**  
 Especifica todos los comandos que se deberán ejecutar antes de que se inicie la compilación.  Para escribir comandos largos, haga clic en **Edición anterior a la compilación** para mostrar el [Línea de comandos del evento anterior\/posterior a la compilación \(Cuadro de diálogo\)](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
> [!NOTE]
>  Los eventos anteriores a la compilación no se ejecutan si el proyecto está actualizado y no se desencadena ninguna generación.  
  
 **Línea de comandos del evento posterior a la compilación**  
 Especifica todos los comandos que se deberán ejecutar después de que finalice la compilación.  Para escribir comandos largos, haga clic en **Edición posterior a la compilación** con el fin de mostrar el cuadro de diálogo **Línea de comandos del evento anterior a la compilación o Línea de comandos del evento posterior a la compilación**.  
  
> [!NOTE]
>  Agregue una instrucción `call` delante de todos los comandos posteriores a la compilación que ejecutan archivos .bat.  Por ejemplo: `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Ejecutar el evento posterior a la compilación**  
 Especifica las condiciones para que se ejecute el evento posterior a la compilación, como se indica en la tabla siguiente.  
  
|Opción|Resultado|  
|------------|---------------|  
|**Siempre**|El evento posterior a la compilación se ejecutará independientemente de si la generación finaliza correctamente.|  
|**Si la compilación es correcta**|El evento posterior a la compilación se ejecutará si la compilación finaliza correctamente.  El evento se ejecutará incluso en un proyecto actualizado, siempre que la compilación finalice correctamente.  Ésta es la configuración predeterminada.|  
|**Cuando la compilación actualiza los resultados del proyecto**|El evento posterior a la compilación solamente se ejecutará cuando el archivo de salida del compilador \(.exe o .dll\) difiera del anterior archivo de salida.  Un evento posterior a la compilación no se ejecutará si se actualiza un proyecto.|  
  
## Vea también  
 [Página Compilación, Diseñador de proyectos \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Cómo: Especificar eventos de compilación \(Visual Basic\)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Línea de comandos del evento anterior\/posterior a la compilación \(Cuadro de diálogo\)](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)