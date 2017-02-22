---
title: "Eventos de compilaci&#243;n (P&#225;gina, Dise&#241;ador de proyectos) (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.ProjectPropertiesBuildEvents"
helpviewer_keywords: 
  - "eventos de compilación"
  - "Diseñador de proyectos, página Eventos de compilación"
  - "eventos anteriores a la compilación"
  - "eventos posteriores a la compilación"
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Eventos de compilaci&#243;n (P&#225;gina, Dise&#241;ador de proyectos) (C#)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La página **Eventos de compilación** del **Diseñador de proyectos** se utiliza para especificar las instrucciones de configuración de compilación.  También puede especificar las condiciones bajo las cuales se ejecutan los eventos posteriores a la compilación.  Para obtener más información, vea [Cómo: Especificar eventos de compilación \(C\#\)](../../ide/how-to-specify-build-events-csharp.md) y [Cómo: Especificar eventos de compilación \(Visual Basic\)](../../ide/how-to-specify-build-events-visual-basic.md).  
  
## Lista de UIElement  
 **Configuración**  
 Este control no se puede modificar en esta página.  Para obtener una descripción de este control, vea [Compilar \(Página, Diseñador de proyectos\) \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Plataforma**  
 Este control no se puede modificar en esta página.  Para obtener una descripción de este control, vea [Compilar \(Página, Diseñador de proyectos\) \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Línea de comandos del evento anterior a la compilación**  
 Especifica todos los comandos que se deberán ejecutar antes de que se inicie la compilación.  Para escribir comandos largos, haga clic en **Edición anterior a la compilación** para mostrar el [Línea de comandos del evento anterior\/posterior a la compilación \(Cuadro de diálogo\)](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
> [!NOTE]
>  Los eventos anteriores a la compilación no se ejecutan si el proyecto está actualizado y no se desencadena ninguna compilación.  
  
 **Línea de comandos del evento posterior a la compilación**  
 Especifica todos los comandos que se deberán ejecutar después de que finalice la compilación.  Para escribir comandos largos, haga clic en **Edición posterior a la compilación** para mostrar el cuadro de diálogo **Línea de comandos del evento anterior a la compilación o Línea de comandos del evento posterior a la compilación**.  
  
> [!NOTE]
>  Agregue una instrucción `call` delante de todos los comandos posteriores a la compilación que ejecutan archivos .bat.  Por ejemplo: `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Ejecutar el evento posterior a la compilación**  
 Especifica las siguientes condiciones para que se ejecute el evento posterior a la compilación, como se indica en la tabla siguiente.  
  
|Opción|Resultado|  
|------------|---------------|  
|**Siempre**|El evento posterior a la compilación se ejecutará independientemente de si la compilación finaliza correctamente.|  
|**Si la compilación es correcta**|El evento posterior a la compilación se ejecutará si la compilación finaliza correctamente.  Así, el evento se ejecutará incluso en un proyecto actualizado, siempre y cuando la compilación finalice correctamente.|  
|**Cuando la compilación actualiza los resultados del proyecto**|El evento posterior a la compilación sólo se ejecutará cuando el archivo de salida del compilador \(.exe o .dll\) difiera del archivo de salida anterior del compilador.  Así, un evento posterior a la compilación no se ejecutará si un proyecto está actualizado.|  
  
## Vea también  
 [Cómo: Especificar eventos de compilación \(Visual Basic\)](../../ide/how-to-specify-build-events-visual-basic.md)   
 [Cómo: Especificar eventos de compilación \(C\#\)](../../ide/how-to-specify-build-events-csharp.md)   
 [Referencia de propiedades del proyecto](../../ide/reference/project-properties-reference.md)   
 [Compilar aplicaciones en Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)