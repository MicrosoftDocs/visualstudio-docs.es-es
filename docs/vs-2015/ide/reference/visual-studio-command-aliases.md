---
title: Alias de comandos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- aliases, Visual Studio commands
- Visual Studio, commands
- predefined command aliases
- commands, aliases
- Visual Studio commands
- pre-defined command aliases
- command aliases
ms.assetid: de8bb378-8c1c-4087-a9a5-537fa8314c19
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7e9419e64cd211490fc1d3785045b5de117d392e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657853"
---
# <a name="visual-studio-command-aliases"></a>Visual Studio Command Aliases
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Los alias permiten escribir un comando en el cuadro **Buscar/Comando** o en la ventana **Comando** acortando el texto necesario para ejecutar el comando. Por ejemplo, en lugar de escribir `>File.OpenFile` para mostrar el cuadro de diálogo **Abrir archivo**, se puede usar el alias predefinido `>of`.

 Escriba `alias` en la ventana **Comandos** para mostrar una lista de los alias actuales y sus definiciones. Escriba `>cls` para borrar el contenido de la ventana **Comando**. Si desea ver un alias para un comando concreto, escriba `alias <command name>`.

 Es fácil crear su propio alias para uno de los comandos de Visual Studio (con o sin argumentos). Por ejemplo, la sintaxis del alias de `File.NewFile MyFile.txt` es `alias MyAlias File.NewFile MyFile.txt`. Se puede eliminar uno de los alias con `alias <alias name> /delete`

 La tabla siguiente contiene una lista de los alias de comando de Visual Studio predefinidos. Algunos nombres de comando tienen más de un alias predefinido. Haga clic en los vínculos de los nombres de comando a continuación para ver temas detallados en los que se explican los modificadores, los argumentos y la sintaxis correcta de dichos comandos.

|Nombre de comando|Alias|Nombre completo|
|------------------|-----------|-------------------|
|[Comando imprimir](../../ide/reference/print-command.md)|?|Debug.Print|
|[Inspección rápida (comando)](../../ide/reference/quick-watch-command.md)|??|Debug.Quickwatch|
|Agregar nuevo proyecto|AddProj|File.AddNewProject|
|[Alias (comando)](../../ide/reference/alias-command.md)|Alias|Tools.Alias|
|Ventana Automático|Autos|Debug.Autos|
|ventana Puntos de interrupción|bl|Debug.Breakpoints|
|Alternar puntos de interrupción|bp|Debug.ToggleBreakPoint|
|Ventana Pila de llamadas|CallStack|Debug.CallStack|
|Borrar marcadores|ClearBook|Edit.ClearBookmarks|
|Cerrar|Cerrar|File.Close|
|Cerrar todos los documentos|CloseAll|Window.CloseAllDocuments|
|Borrar todo|cls|Edit.ClearAll|
|Modo Comando|cmd|View.CommandWindow|
|Ver código|código|View.ViewCode|
|[Comando Mostrar memoria](../../ide/reference/list-memory-command.md)|d|Debug.ListMemory|
|[Comando Mostrar memoria](../../ide/reference/list-memory-command.md) como ANSI|da|Debug.ListMemory /Ansi|
|[Comando Mostrar memoria](../../ide/reference/list-memory-command.md) con formato de un byte|db|Debug.ListMemory /Format:OneByte|
|[Comando Mostrar memoria](../../ide/reference/list-memory-command.md) como ANSI con formato de cuatro bytes|dc|Debug.ListMemory /Format:FourBytes /Ansi|
|[Comando Mostrar memoria](../../ide/reference/list-memory-command.md) con formato de cuatro bytes|dd|Debug.ListMemory /Format:FourBytes|
|Eliminar hasta principio de línea|DelBOL|Edit.DeleteToBOL|
|Eliminar hasta final de línea|DelEOL|Edit.DeleteToEOL|
|Eliminar espacio en blanco horizontal|DelHSp|Edit.DeleteHorizontalWhitespace|
|Diseñador de vistas|designer|View.ViewDesigner|
|[Comando Mostrar memoria](../../ide/reference/list-memory-command.md) con formato flotante|df|Debug.ListMemory/Format:Float|
|ventana Desensamblado|disasm|Debug.Disassembly|
|[Comando Mostrar memoria](../../ide/reference/list-memory-command.md) con formato de ocho bytes|dq|Debug.ListMemory /Format:EightBytes|
|[Comando Mostrar memoria](../../ide/reference/list-memory-command.md) como Unicode|du|Debug.ListMemory /Unicode|
|[Evaluar instrucción (comando)](../../ide/reference/evaluate-statement-command.md)|eval|Debug.EvaluateStatement|
|Salir|Salir|File.Exit|
|Dar formato a la selección|format|Edit.FormatSelection|
|Pantalla completa|FullScreen|View.FullScreen|
|[Iniciar (comando)](../../ide/reference/start-command.md)|g|Debug.Start|
|[Ir a (comando)](../../ide/reference/go-to-command.md)|GotoLn|Edit.GoTo|
|Ir a llave|GotoBrace|Edit.GotoBrace|
|F1Help|Ayuda|Help.F1Help|
|Modo inmediato|immed|Tools.ImmediateMode|
|Insertar archivo como texto|InsertFile|Edit.InsertFileAsText|
|[Comando Mostrar pila de llamadas](../../ide/reference/list-call-stack-command.md)|kb|Debug.ListCallStack|
|Poner en minúsculas|Lcase|Edit.MakeLowercase|
|Cortar línea|LineCut|Edit.LineCut|
|Eliminar línea|LineDel|Edit.LineDelete|
|Lista de miembros|ListMembers|Edit.ListMembers|
|Ventana Locales|Locals|Debug.Locals|
|[Comando registrar resultado de la ventana comandos](../../ide/reference/log-command-window-output-command.md)|Log|Tools.LogCommandWindowOutput|
|Modo Marcar ventana de comandos|mark|Tools.CommandWindowMarkMode|
|Ventana Memoria|Memory Memory1|Debug.Memory1|
|Ventana Memoria 2|Memory2|Debug.Memory2|
|Ventana Memoria 3|Memory3|Debug.Memory3|
|Ventana Memoria 4|Memory4|Debug.Memory4|
|[Establecer base (comando)](../../ide/reference/set-radix-command.md)|n|Debug.SetRadix|
|[Comando Showwebbrowser (](../../ide/reference/showwebbrowser-command.md)|nav navigate|View.ShowWebBrowser|
|Marcador siguiente|NextBook|Edit.NextBookmark|
|[Comando nuevo archivo](../../ide/reference/new-file-command.md)|nf|File.NewFile|
|Nuevo proyecto|np NewProj|File.NewProject|
|[Abrir archivo (comando)](../../ide/reference/open-file-command.md)|of Open|File.OpenFile|
|[Abrir proyecto (comando)](../../ide/reference/open-project-command.md)|op|File.OpenProject|
|Contraer a definiciones/Detener esquematización|OutlineDefs StopOutlining|Edit.CollapsetoDefinitions|
|Paso a paso por procedimientos|p|Debug.StepOver|
|Información de parámetros|ParamInfo|Edit.ParameterInfo|
|Depurar paso a paso para salir|pr|Debug.StepOut|
|Marcador anterior|PrevBook|Edit.PreviousBookmark|
|Imprimir archivo|imprimir|File.Print|
|Ventana Propiedades|props|View.PropertiesWindow|
|Stop|q|Debug.StopDebugging|
|Rehacer|rehacer|Edit.Redo|
|Ventana Registros|registers|Debug.Registers|
|Ejecutar hasta el cursor|rtc|Debug.RunToCursor|
|Guardar los elementos seleccionados|Guardar|File.SaveSelectedItems|
|Guardar todo|SaveAll|File.SaveAll|
|Guardar como|SaveAs|File.SaveSelectedItemsAs|
|[Comando de Shell](../../ide/reference/shell-command.md)|shell|Tools.Shell|
|Detener Buscar en archivos|StopFind|Edit.FindInFiles /stop|
|Cambiar delimitador|SwapAnchor|Edit.SwapAnchor|
|Paso a paso por instrucciones|t|Debug.StepInto|
|Aplicar tabulación a la selección|tabify|Edit.TabifySelection|
|Ventana Lista de tareas|TaskList|View.TaskList|
|Ventana Subprocesos|Subprocesos|Debug.Threads|
|Mosaico horizontal|TileH|Window.TileHorizontally|
|Mosaico vertical|TileV|Window.TileVertically|
|Alternar marcador|ToggleBook|Edit.ToggleBookmark|
|Ventana Cuadro de herramientas|cuadro de herramientas|View.Toolbox|
|[Mostrar desensamblador (comando)](../../ide/reference/list-disassembly-command.md)|u|Debug.ListDisassembly|
|Poner en mayúsculas|Ucase|Edit.MakeUppercase|
|Deshacer|deshacer|Edit.Undo|
|Quitar tabulación a la selección|Untabify|Edit.UntabifySelection|
|Ventana Inspección|Watch|Debug.WatchN|
|Alternar ajuste de línea|WordWrap|Edit.ToggleWordWrap|
|Mostrar procesos|&#124;|Debug.ListProcesses|
|[Comando Mostrar subprocesos](../../ide/reference/list-threads-command.md)|~ ~*k ~\*kb|Debug.ListThreads Debug.ListTheads /AllThreads|

## <a name="see-also"></a>Consulte también
 Cuadro de comandos [Buscar/comando](../../ide/find-command-box.md) de la [ventana](../../ide/reference/command-window.md) comandos de [Visual Studio](../../ide/reference/visual-studio-commands.md)
