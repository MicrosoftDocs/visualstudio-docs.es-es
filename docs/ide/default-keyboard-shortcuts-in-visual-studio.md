---
title: Métodos abreviados de teclado predeterminados
description: Conozca los métodos abreviados de teclado predeterminados de Visual Studio que le permiten acceder a diversos comandos y ventanas.
ms.custom: SEO-VS-2020
ms.date: 06/21/2021
ms.topic: reference
helpviewer_keywords:
- shortcut keys [Visual Studio], keyboard binding schemes
- keyboard binding schemes [Visual Studio]
- Help [Visual Studio], shortcut keys
- keyboard shortcuts [Visual Studio], keyboard binding schemes
- keyboard shortcuts
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dec9f76f2b21e11cc79bc55efc4a2de6fb7dedc3
ms.sourcegitcommit: 15821c790d6498210f30b3268402ffad6bb70c7c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2021
ms.locfileid: "113725526"
---
# <a name="default-keyboard-shortcuts-in-visual-studio"></a>Métodos abreviados de teclado predeterminados de Visual Studio

Puede acceder a una serie de [comandos](reference/visual-studio-commands.md) y ventanas en Visual Studio eligiendo el acceso directo de teclado correspondiente. En esta página se indican los accesos directos predeterminados para el perfil **General**, que tal vez haya elegido al instalar Visual Studio. Independientemente del perfil que haya elegido, puede [identificar el acceso directo](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) de un comando abriendo el cuadro de diálogo **Opciones**, expandiendo el nodo **Entorno** y, después, pulsando **Teclado**. También puede personalizar los métodos abreviados de teclado asignando un método abreviado diferente a un determinado comando.

Para obtener una lista de los accesos directos de teclado comunes y otra información de productividad, consulte:

- [Sugerencias y trucos de Visual Studio](../ide/productivity-shortcuts.md)
- [Sugerencias de productividad](../ide/productivity-features.md).

Para obtener más información sobre la accesibilidad en Visual Studio, consulte [Sugerencias y trucos de accesibilidad](../ide/reference/accessibility-tips-and-tricks.md) y [Cómo: Usar el teclado exclusivamente](../ide/reference/how-to-use-the-keyboard-exclusively.md).

<a name="popular"></a>
## <a name="popular-keyboard-shortcuts-for-visual-studio"></a>Métodos abreviados de teclado de uso frecuente para Visual Studio

Todos los métodos abreviados de teclado de esta sección se aplican de forma global a menos que se especifique lo contrario. El contexto *Global* significa que el método abreviado puede aplicarse en cualquier ventana de herramientas de Visual Studio.

> [!NOTE]
> Puede [buscar el método abreviado](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) de un comando abriendo el cuadro de diálogo **Opciones**, expandiendo el nodo **Entorno** y eligiendo **Teclado**.


#### <a name="build-popular-shortcuts"></a>Compilación: métodos abreviados de teclado populares

|Comandos|Métodos abreviados de teclado |Identificador de comando|
|-|-|-|
|Compilar la solución|**Ctrl+Mayús+B** | Build.BuildSolution |
|Cancelar|**Ctrl+Inter** | Build.Cancel |
|Compile|**Ctrl+F7** | Build.Compile |
|Ejecutar análisis de código en la solución|**Alt+F11**| Build.RunCodeAnalysisonSolution |

#### <a name="debug-popular-shortcuts"></a>Depuración: métodos abreviados de teclado populares

|Comandos|Métodos abreviados de teclado [contextos especiales]|Identificador de comando|
|-|-|-|
|Interrumpir en una función|**Ctrl+B**| Debug.BreakatFunction |
|Interrumpir todos|**Ctrl+Alt+Inter**| Debug.BreakAll |
|Eliminar todos los puntos de interrupción|**Ctrl+Mayús+F9**| Debug.DeleteAllBreakpoints |
|Excepciones|**Ctrl+Alt+E**| Debug.Exceptions |
|Inspección rápida|**Ctrl+Alt+Q**<br /><br />o bien **Mayús+F9**| Debug.QuickWatch |
|Reiniciar|**Ctrl+Mayús+F5**| Debug.Restart |
|Ejecutar hasta el cursor|**Ctrl+F10**| Debug.RunToCursor |
|Establecer instrucción siguiente|**Ctrl+Mayús+F10**| Debug.SetNextStatement |
|Inicio|**F5**| Debug.Start |
|Iniciar sin depurar|**Ctrl+F5**| Debug.StartWithoutDebugging |
|Paso a paso por instrucciones|**F11**| Debug.StepInto |
|Salida de la depuración|**Mayús+F11**| Debug.StepOut |
|Paso a paso por procedimientos|**F10**| Debug.StepOver |
|Detener depuración|**Mayús+F5**| Debug.StopDebugging |
|Alternar puntos de interrupción|**F9**| Debug.ToggleBreakpoint |

#### <a name="edit-popular-shortcuts"></a>Edición: métodos abreviados de teclado populares

|Comandos|Métodos abreviados de teclado [contextos especiales]|Identificador de comando|
|-|-|-|
|Dividir línea|**Entrar** [Editor de texto, Diseñador de informes, Diseñador de Windows Forms]<br /><br />o **Mayús+Entrar** [Editor de texto]| Edit.BreakLine |
|Contraer a definiciones|**Ctrl+M**, **Ctrl+O** [Editor de texto]| Edit.CollapseToDefinitions |
|Comentar selección|**Ctrl+K**, **Ctrl+C** [Editor de texto]| Edit.CommentSelection |
|Completar palabra|**Alt+Flecha derecha** [Editor de texto, Diseñador de flujo de trabajo]<br /><br />o **Ctrl+Barra espaciadora** [Editor de texto, Diseñador de flujo de trabajo]<br /><br />o **Ctrl+K**, **W** [Diseñador de flujo de trabajo]<br /><br />o **Ctrl+K, Ctrl+W** [Diseñador de flujo de trabajo]| Edit.CompleteWord |
|Copiar|**Ctrl+C**<br /><br />o bien **Ctrl+Insert**| Edit.Copy |
|Cortar|**Ctrl+X**<br /><br />o bien **Mayús+Supr**| Edit.Cut |
|Eliminar|**Eliminar** [Team Explorer]<br /><br />o **Mayús+Supr** [Diagrama de secuencia, Diagrama de actividades de UML, Diagramas de capas]<br /><br />o **Ctrl+Supr** [Diagrama de clases]| Edit.Delete |
|Buscar|**Ctrl+F**| Edit.Find |
|Buscar todas las referencias|**Mayús+F12**| Edit.FindAllReferences |
|Buscar en archivos|**Ctrl+Mayús+F**| Edit.FindinFiles |
|Buscar siguiente|**F3**| Edit.FindNext |
|Buscar el siguiente seleccionado|**Ctrl+F3**| Edit.FindNextSelected |
|Aplicación de formato al documento|**Ctrl+K, Ctrl+D** [Editor de texto]| Edit.FormatDocument |
|Aplicación de formato a la selección|**Ctrl+K, Ctrl+F** [Editor de texto]| Edit.FormatSelection |
|Ir a|**Ctrl+G**| Edit.GoTo |
|Ir a declaración|**Ctrl+F12**| Edit.GoToDeclaration |
|Ir a definición|**F12**| Edit.GoToDefinition |
|Ir al cuadro combinado Buscar|**Ctrl+D**| Edit.GoToFindCombo |
|Ir a la ubicación siguiente|**F8**| Edit.GoToNextLocation |
|Insertar fragmento de código|**Ctrl+K**, **Ctrl+X**| Edit.InsertSnippet |
|Pestaña Insertar|**Tabulación** [Diseñador de informes, Diseñador de Windows Forms, Editor de texto]| Edit.InsertTab |
|Cortar línea|**Ctrl+L** [Editor de texto]| Edit.LineCut |
|Extender columna una línea abajo|**Mayús+Alt+Flecha abajo** [Editor de texto]| Edit.LineDownExtendColumn |
|Abrir línea encima|**Ctrl+Entrar** [Editor de texto]| Edit.LineOpenAbove |
|Enumerar miembros|**Ctrl+J** [Editor de texto, Diseñador de flujo de trabajo]<br /><br />o **Ctrl+K, Ctrl+L** [Diseñador de flujo de trabajo]<br /><br />o **Ctrl+K, L** [Diseñador de flujo de trabajo]| Edit.ListMembers |
|Navegar a|**Ctrl+,**| Edit.NavigateTo |
|Abrir archivo|**Ctrl+Mayús+G**| Edit.OpenFile |
|Modo de reemplazo|**Insert** [Editor de texto]| Edit.OvertypeMode |
|Información de parámetros|**Ctrl+Mayús+Barra espaciadora** [Editor de texto, Diseñador de flujo de trabajo]<br /><br />o **Ctrl+K, Ctrl+P** [Diseñador de flujo de trabajo]<br /><br />o **Ctrl+K, P** [Diseñador de flujo de trabajo]| Edit.ParameterInfo |
|Pegar|**Ctrl+V**<br /><br />o bien **Mayús+Insertar**| Edit.Paste |
|Ver la definición sin salir|**Alt+F12** [Editor de texto]| Edit.PeekDefinition |
|Rehacer|**Ctrl+Y**<br /><br />o bien **Mayús+Alt+Retroceso**<br /><br />o bien **Ctrl+Mayús+Z**| Edit.Redo |
|Replace|**Ctrl+H**| Edit.Replace |
|Seleccionar todo|**Ctrl+A**| Edit.SelectAll |
|Seleccionar palabra actual|**Ctrl+W** [Editor de texto]| Edit.SelectCurrentWord |
|Cancelar selección|**Esc** [Editor de texto, Diseñador de informes, Diseñador de configuración, Diseñador de Windows Forms, Editor de recursos administrados]| Edit.SelectionCancel |
|Rodear con|**Ctrl+K, Ctrl+S**| Edit.SurroundWith |
|Tabulación a la izquierda|**Mayús+Tab** [Editor de texto, Diseñador de informes, Editor de formularios Windows Forms]| Edit.TabLeft |
|Alternar toda la esquematización|**Ctrl+M, Ctrl+L** [Editor de texto]| Edit.ToggleAllOutlining |
|Alternar marcador|**Ctrl+K, Ctrl+K** [Editor de texto]| Edit.ToggleBookmark |
|Alternar el modo de finalización|**Ctrl+Alt+Barra espaciadora** [Editor de texto]| Edit.ToggleCompletionMode |
|Alternar expansión de esquematización|**Ctrl+M, Ctrl+M** [Editor de texto]| Edit.ToggleOutliningExpansion |
|Selección sin comentarios|**Ctrl+K, Ctrl+U** [Editor de texto]| Edit.UncommentSelection |
|Deshacer|**Ctrl+Z**<br /><br />o bien **Alt+Retroceso**| Edit.Undo |
|Eliminar hasta el final de la palabra|**Ctrl+Supr** [Editor de texto]| Edit.WordDeleteToEnd |
|Eliminar hasta el principio de la palabra|**Ctrl+Retroceso** [Editor de texto]| Edit.WordDeleteToStart |

#### <a name="file-popular-shortcuts"></a>Archivo: métodos abreviados de teclado populares

|Comandos|Métodos abreviados de teclado [contextos especiales]|Identificador de comando|
|-|-|-|
|Salir|**Alt+F4**| File.Exit |
|Nuevo archivo|**Ctrl+N**| File.NewFile |
|Nuevo proyecto|**Ctrl+Mayús+N**| File.NewProject |
|Nuevo sitio web|**Mayús+Alt+N**| File.NewWebSite |
|Abrir archivo|**Ctrl+O**| File.OpenFile |
|Abrir el proyecto|**Ctrl+Mayús+O**| File.OpenProject |
|Abrir sitio web|**Mayús+Alt+O**| File.OpenWebSite |
|Cambiar nombre|**F2** [Team Explorer]| File.Rename |
|Guardar todo|**Ctrl+Mayús+S**| File.SaveAll |
|Guardar elementos seleccionados|**Ctrl+S**| File.SaveSelectedItems |
|Visualización en un explorador|**Ctrl+Mayús+W**| File.ViewinBrowser |

#### <a name="project-popular-shortcuts"></a>Proyecto: métodos abreviados de teclado populares

|Comandos|Métodos abreviados de teclado [contextos especiales]|Identificador de comando|
|-|-|-|
|Agregar elemento existente|**Mayús+Alt+A**| Project.AddExistingItem |
|Agregar un nuevo elemento|**Ctrl+Mayús+A**| Project.AddNewItem |

#### <a name="refactor-popular-shortcuts"></a>Refactorizar: métodos abreviados de teclado populares

|Comando|Método abreviado de teclado [contextos especiales]|Identificador de comando|
|-|-|-|
|Extraer método|**Ctrl+R, Ctrl+M**| Refactor.ExtractMethod |

#### <a name="tools-popular-shortcuts"></a>Herramientas: métodos abreviados de teclado populares

|Comando|Método abreviado de teclado [contextos especiales]|Identificador de comando|
|-|-|-|
|Asociar al proceso|**Ctrl+Alt+P**| Tools.AttachtoProcess |

#### <a name="view-popular-shortcuts"></a>Ver: métodos abreviados de teclado populares

|Comandos|Métodos abreviados de teclado [contextos especiales]|Identificador de comando|
|-|-|-|
|Vista de clases|**Ctrl+Mayús+C**| View.ClassView |
|Editar etiqueta|**F2**| View.EditLabel |
|Lista de errores|**Ctrl+\\, Ctrl+E**<br /><br />o bien **Ctrl+\\, E**| View.ErrorList |
|Navegar hacia atrás|**Ctrl+-**| View.NavigateBackward |
|Navegar hacia adelante|**Ctrl+Mayús+-**| View.NavigateForward |
|Explorador de objetos|**Ctrl+Alt+J**| View.ObjectBrowser |
|Output|**Ctrl+Alt+O**| View.Output |
|Propiedades (ventana)|**F4**| View.PropertiesWindow |
|Actualizar|**F5** [Team Explorer]| View.Refresh |
|Explorador de servidores|**Ctrl+Alt+S**| View.ServerExplorer |
|Mostrar etiqueta inteligente|**Ctrl+.**<br /><br />o bien **Mayús+Alt+F10** [Vista de diseño del editor de HTML]| View.ShowSmartTag |
|Explorador de soluciones|**Ctrl+Alt+L**| View.SolutionExplorer |
|Team Explorer de TFS|**Ctrl+\\, Ctrl+M**| View.TfsTeamExplorer |
|Cuadro de herramientas|**Ctrl+Alt+X**| View.Toolbox |
|Ver código|**Entrar** [Diagrama de clases]<br /><br />o **F7** [Diseñador de configuración]| View.ViewCode |
|Diseñador de vistas|**Mayús+F7** [Vista de código fuente del editor de HTML]| View.ViewDesigner |

#### <a name="window-popular-shortcuts"></a>Ventana: métodos abreviados de teclado populares

|Comandos|Métodos abreviados de teclado [contextos especiales]|Identificador de comando|
|-|-|-|
|Activar ventana de documento|**Esc**| Window.ActivateDocumentWindow |
|Cerrar la ventana de documento|**Ctrl+F4**| Window.CloseDocumentWindow |
|Ventana de documento siguiente|**Ctrl+F6**| Window.NextDocumentWindow |
|Ir a ventana de documento siguiente|**Ctrl+Tab**| Window.NextDocumentWindowNav |
|Panel de división siguiente|**F6**| Window.NextSplitPane |


## <a name="global-shortcuts"></a>Accesos directos globales

Estos métodos abreviados de teclado son *globales*, lo que significa que se pueden usar cuando tenga el foco cualquier ventana de Visual Studio.

- [Analizar](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_analyze)
- [Editar](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_edit)
- [Proyecto](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_project)
- [Prueba](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_test)
- [Arquitectura](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_architecture)
- [Menús contextuales del editor](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_editorContext)
- [Menús contextuales de proyectos y soluciones](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_projectContext)
- [Explorador de pruebas](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL)
- [Compilación](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_build)
- [Archivo](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_file)
- [Refactorizar](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_refactor)
- [Herramientas](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_tools)
- [Menús contextuales de vistas de clases](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_classview)
- [Ayuda](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_help)
- [Explorador de soluciones](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)
- [Vista](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view)
- [Depurar](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debug)
- [Prueba de carga](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_loadtest)
- [Equipo](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_team)
- [Ventana](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_window)
- [Menús contextuales del depurador](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debugger)
- [Otros menús contextuales](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_otherContext)
- [Menús contextuales de Team Foundation](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TFcontext)
- [Azure](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_windowsazure)
- [Concentrador de diagnósticos](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_diagnostics)

### <a name="analyze"></a><a name="bkmk_analyze"></a> Analizar

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Navegar hacia atrás|**Mayús+Alt+3**| Analyze.NavigateBackward |
|Navegar hacia adelante|**Mayús+Alt+4**| Analyze.NavigateForward |

### <a name="architecture"></a><a name="bkmk_architecture"></a> Arquitectura

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Nuevo diagrama|**Ctrl+\\, Ctrl+N**| Architecture.NewDiagram |

### <a name="build"></a><a name="bkmk_build"></a> Compilación

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Compilar selección|**Ctrl + B** (Visual Studio 2019)| Build.BuildSelection |
|Compilar la solución|**Ctrl+Mayús+B**| Build.BuildSolution |
|Cancelar|**Ctrl+Inter**| Build.Cancel |
|Compile|**Ctrl+F7**| Build.Compile |
|Ejecutar análisis de código en la solución|**Alt+F11**| Build.RunCodeAnalysisonSolution |

### <a name="class-view-context-menus"></a><a name="bkmk_classview"></a> Menús contextuales de vistas de clases

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Propiedades|**Alt+Entrar**| ClassViewContextMenus.ClassViewMultiselectProjectreferencesItems.Properties |

### <a name="debug"></a><a name="bkmk_debug"></a> Depurar

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Aplicar cambios de código|**Alt+F10**| Debug.ApplyCodeChanges |
|Asociar al proceso|**Ctrl+Alt+P**| Debug.AttachtoProcess |
|Autos|**Ctrl+Alt+V, A**| Debug.Autos |
|Interrumpir todos|**Ctrl+Alt+Inter**| Debug.BreakAll |
|Puntos de interrupción|**Ctrl+Alt+B**| Debug.Breakpoints |
|Pila de llamadas|**Ctrl+Alt+C**| Debug.CallStack |
|Eliminar todos los puntos de interrupción|**Ctrl+Mayús+F9**| Debug.DeleteAllBreakpoints |
|Launch|**Alt+F2**| Debug.DiagnosticsHub.Launch |
|Desensamblado|**Ctrl+Alt+D**| Debug.Disassembly |
|Explorador DOM|**Ctrl+Alt+V, D**| Debug.DOMExplorer |
|Habilitar puntos de interrupción|**Ctrl+F9**| Debug.EnableBreakpoints |
|Excepciones|**Ctrl+Alt+E**| Debug.Exceptions |
|Punto de interrupción de función|**Ctrl + K, B** (Visual Studio 2019)<br />**Ctrl**+**B** (Visual Studio 2017)| Debug.FunctionBreakpoint |
|Ir a llamada o evento de IntelliTrace anterior|**Ctrl+Mayús+F11**| Debug.GoToPreviousCallorIntelliTraceEvent |
|Iniciar diagnósticos|**Alt+F5**| Debug.Graphics.StartDiagnostics |
|Inmediata|**Ctrl+Alt+I**| Debug.Immediate |
|Llamadas de IntelliTrace|**Ctrl+Alt+Y, T**| Debug.IntelliTraceCalls |
|Eventos de IntelliTrace|**Ctrl+Alt+Y, F**| Debug.IntelliTraceEvents |
|Consola de JavaScript|**Ctrl+Alt+V, C**| Debug.JavaScriptConsole |
|Locals|**Ctrl+Alt+V, L**| Debug.Locals |
|Cuadro combinado Proceso|**Ctrl+5**| Debug.LocationToolbar.ProcessCombo |
|Cuadro combinado Marco de pila|**Ctrl+7**| Debug.LocationToolbar.StackFrameCombo |
|Cuadro combinado Subproceso|**Ctrl+6**| Debug.LocationToolbar.ThreadCombo |
|Alternar estado marcado del subproceso actual|**Ctrl+8**| Debug.LocationToolbar.ToggleCurrentThreadFlaggedState |
|Alternar subprocesos marcados|**Ctrl+9**| Debug.LocationToolbar.ToggleFlaggedThreads |
|Memoria 1|**Ctrl+Alt+M, 1**| Debug.Memory1 |
|Memoria 2|**Ctrl+Alt+M, 2**| Debug.Memory2 |
|Memoria 3|**Ctrl+Alt+M, 3**| Debug.Memory3 |
|Memoria 4|**Ctrl+Alt+M, 4**| Debug.Memory4 |
|Módulos|**Ctrl+Alt+U**| Debug.Modules |
|Pilas paralelas|**Ctrl+Mayús+D, S**| Debug.ParallelStacks |
|Inspección paralela 1|**Ctrl+Mayús+D, 1**| Debug.ParallelWatch1 |
|Inspección paralela 2|**Ctrl+Mayús+D, 2**| Debug.ParallelWatch2 |
|Inspección paralela 3|**Ctrl+Mayús+D, 3**| Debug.ParallelWatch3 |
|Inspección paralela 4|**Ctrl+Mayús+D, 4**| Debug.ParallelWatch4 |
|Procesos|**Ctrl+Alt+Z**| Debug.Processes |
|Inspección rápida|**Mayús + F9** o **Ctrl + Al t+ Q**| Debug.QuickWatch |
|Reasociar al proceso|**Mayús+Alt+P**| Debug.ReattachtoProcess |
|Actualizar aplicación de Windows|**Ctrl+Mayús+R**| Debug.RefreshWindowsapp |
|Registros|**Ctrl+Alt+G**| Debug.Registers |
|Reiniciar|**Ctrl+Mayús+F5**| Debug.Restart |
|Ejecutar hasta el cursor|**Ctrl+F10**| Debug.RunToCursor |
|Establecer instrucción siguiente|**Ctrl+Mayús+F10**| Debug.SetNextStatement |
|Mostrar pila de llamadas en mapa de código|**Ctrl+Mayús+`**| Debug.ShowCallStackonCodeMap |
|Mostrar la instrucción siguiente|**Alt+Núm** *| Debug.ShowNextStatement |
|Inicio|**F5**| Debug.Start |
|Iniciar análisis de aplicación de Windows Phone|**Alt+F1**| Debug.StartWindowsPhoneApplicationAnalysis |
|Iniciar sin depurar|**Ctrl+F5**| Debug.StartWithoutDebugging |
|Paso a paso por instrucciones|**F11**| Debug.StepInto |
|Ir al proceso actual|**Ctrl+Alt+F11**| Debug.StepIntoCurrentProcess |
|Ir a específico|**Mayús+Alt+F11**| Debug.StepIntoSpecific |
|Salida de la depuración|**Mayús+F11**| Debug.StepOut |
|Paso a paso para salir del procedimiento actual|**Ctrl+Mayús+Alt+F11**| Debug.StepOutCurrentProcess |
|Paso a paso por procedimientos|**F10** (al depurar: realiza una acción de paso a paso por procedimientos)| Debug.StepOver |
|Paso a paso por procedimientos|**F10** (cuando no se está depurando: inicia la depuración y se detiene en la primera línea del código de usuario)| Debug.StepOver |
|Paso a paso por el proceso actual|**Ctrl+Alt+F10**| Debug.StepOverCurrentProcess |
|Detener depuración|**Mayús+F5**| Debug.StopDebugging |
|Detener análisis de rendimiento|**Mayús+Alt+F2**| Debug.StopPerformanceAnalysis |
|Tareas|**Ctrl+Mayús+D, K**| Debug.Tasks |
|Subprocesos|**Ctrl+Alt+H**| Debug.Threads |
|Alternar puntos de interrupción|**F9**| Debug.ToggleBreakpoint |
|Alternar desensamblado|**Ctrl+F11**| Debug.ToggleDisassembly |
|Inspección 1|**Ctrl+Alt+W, 1**| Debug.Watch1 |
|Inspección 2|**Ctrl+Alt+W, 2**| Debug.Watch2 |
|Inspección 3|**Ctrl+Alt+W, 3**| Debug.Watch3 |
|Inspección 4|**Ctrl+Alt+W, 4**| Debug.Watch4 |

### <a name="debugger-context-menus"></a><a name="bkmk_debugger"></a> Menús contextuales del depurador

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Eliminar|**Alt+F9, D**| DebuggerContextMenus.BreakpointsWindow.Delete |
|Ir al desensamblado|**Alt+F9, A**| DebuggerContextMenus.BreakpointsWindow.GoToDisassembly |
|Ir al código fuente|**Alt+F9, S**| DebuggerContextMenus.BreakpointsWindow.GoToSourceCode |

### <a name="diagnostics-hub"></a><a name="bkmk_diagnostics"></a> Concentrador de diagnósticos

|Comando|Método abreviado de teclado|Identificador de comando|
|-|-|-|
|Detención de la recopilación|**Ctrl+Alt+F2**| DiagnosticsHub.StopCollection |

### <a name="edit"></a><a name="bkmk_edit"></a> Editar

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Copiar|**Ctrl+C**<br /><br /> o<br /><br /> **Ctrl+Insert**| Edit.Copy |
|Cortar|**Ctrl+X**<br /><br /> o<br /><br /> **Mayús+Supr**| Edit.Cut |
|Recorrer el Portapapeles|**Ctrl+Mayús+V**<br /><br /> o<br /><br /> **Ctrl+Mayús+Insert**| Edit.CycleClipboardRing |
|Eliminar|**Eliminar**| Edit.Delete |
|Duplicar|**Ctrl+D**| Edit.Duplicate |
|Buscar|**Ctrl+F**| Edit.Find |
|Buscar todas las referencias|**Mayús+F12**| Edit.FindAllReferences |
|Buscar en archivos|**Ctrl+Mayús+F**| Edit.FindinFiles |
|Buscar siguiente|**F3**| Edit.FindNext |
|Buscar el siguiente seleccionado|**Ctrl+F3**| Edit.FindNextSelected |
|Buscar anterior|**Mayús+F3**| Edit.FindPrevious |
|Buscar el anterior seleccionado|**Ctrl+Mayús+F3**| Edit.FindPreviousSelected |
|Generar método|**Ctrl+K, Ctrl+M**| Edit.GenerateMethod |
|Ir a|**Ctrl+G**| Edit.GoTo |
|Ir a todo|**Ctrl+,** o **Ctrl+T**| Edit.GotoAll |
|Ir a declaración|**Ctrl+F12**| Edit.GoToDeclaration |
|Ir a definición|**F12**| Edit.GoToDefinition |
|Ir al miembro|**Ctrl+1, Ctrl+M** o **Ctrl+1, M** o **Alt+\\**| Edit.GoToMember |
|Ir a la ubicación siguiente|**F8** (Error siguiente en la ventana Lista de errores o Salida)| Edit.GoToNextLocation |
|Ir a la ubicación anterior|**Mayús+F8** (Error anterior en la ventana Lista de errores o Salida)| Edit.GoToPrevLocation |
|Insertar fragmento de código|**Ctrl+K, Ctrl+X**| Edit.InsertSnippet |
|Mover control hacia abajo|**Ctrl+Flecha abajo**| Edit.MoveControlDown |
|Mover control hacia abajo a la cuadrícula|**Flecha abajo**| Edit.MoveControlDownGrid |
|Mover el control a la izquierda|**Ctrl+Flecha izquierda**| Edit.MoveControlLeft |
|Mover control a la izquierda a la cuadrícula|**Flecha izquierda**| Edit.MoveControlLeftGrid |
|Mover el control a la derecha|**Ctrl+Flecha derecha**| Edit.MoveControlRight |
|Mover control a la derecha a la cuadrícula|**Flecha derecha**| Edit.MoveControlRightGrid |
|Mover control hacia arriba|**Ctrl+Flecha arriba**| Edit.MoveControlUp |
|Mover control hacia arriba a la cuadrícula|**Flecha arriba**| Edit.MoveControlUpGrid |
|Marcador siguiente|**Ctrl+K, Ctrl+N**| Edit.NextBookmark |
|Marcador siguiente en carpeta|**Ctrl+Mayús+K, Ctrl+Mayús+N**| Edit.NextBookmarkInFolder |
|Abrir archivo|**Ctrl+Mayús+G** (Abre el nombre de archivo bajo el cursor)| Edit.OpenFile |
|Pegar|**Ctrl+V**<br /><br /> o<br /><br /> **Mayús+Insert**| Edit.Paste |
|Marcador anterior|**Ctrl+K, Ctrl+P**| Edit.PreviousBookmark |
|Marcador anterior en carpeta|**Ctrl+Mayús+K, Ctrl+Mayús+P**| Edit.PreviousBookmarkInFolder |
|Búsqueda rápida de símbolos|**Mayús+Alt+F12**| Edit.QuickFindSymbol |
|Rehacer|**Ctrl+Y**<br /><br /> o<br /><br /> **Ctrl+Mayús+Z**<br /><br /> o<br /><br /> **Mayús+Alt+Retroceso**| Edit.Redo |
|Actualizar referencias remotas|**Ctrl+Mayús+J**| Edit.RefreshRemoteReferences |
|Replace|**Ctrl+H**| Edit.Replace |
|Reemplazar en archivos|**Ctrl+Mayús+H**| Edit.ReplaceinFiles |
|Seleccionar todo|**Ctrl+A**| Edit.SelectAll |
|Seleccionar control siguiente|**Tabulación**| Edit.SelectNextControl |
|Seleccionar control anterior|**Mayús+Tab**| Edit.SelectPreviousControl |
|Mostrar cuadrícula de mosaico|**Entrar**| Edit.ShowTileGrid |
|Ajustar tamaño de control por abajo|**Ctrl+Mayús+Flecha abajo**| Edit.SizeControlDown |
|Ajustar tamaño de control hacia abajo a la cuadrícula|**Mayús+Flecha abajo**| Edit.SizeControlDownGrid |
|Ajustar tamaño de control por la izquierda|**Ctrl+Mayús+Flecha izquierda**| Edit.SizeControlLeft |
|Ajustar tamaño de control a la izquierda a la cuadrícula|**Mayús+Flecha izquierda**| Edit.SizeControlLeftGrid |
|Ajustar tamaño de control por la derecha|**Ctrl+Mayús+Flecha derecha**| Edit.SizeControlRight |
|Ajustar tamaño de control a la derecha a la cuadrícula|**Mayús+Flecha derecha**| Edit.SizeControlRightGrid |
|Ajustar tamaño de control por arriba|**Ctrl+Mayús+Flecha arriba**| Edit.SizeControlUp |
|Ajustar tamaño de control hacia arriba a la cuadrícula|**Mayús+Flecha arriba**| Edit.SizeControlUpGrid |
|Detener búsqueda|**Alt+F3, S**| Edit.StopSearch |
|Rodear con|**Ctrl+K, Ctrl+S**| Edit.SurroundWith |
|Deshacer|**Ctrl+Z**<br /><br /> o<br /><br /> **Alt+Retroceso**| Edit.Undo |

### <a name="editor-context-menus"></a><a name="bkmk_editorContext"></a> Menús contextuales del editor

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Condiciones de punto de interrupción|**Alt+F9, C**| EditorContextMenus.CodeWindow.Breakpoint.BreakpointConditions |
|Etiquetas de edición de puntos de interrupción|**Alt+F9, L**| EditorContextMenus.CodeWindow.Breakpoint.BreakpointEditlabels |
|Mostrar elemento|**Ctrl+`**| EditorContextMenus.CodeWindow.CodeMap.ShowItem |
|Execute|**Ctrl+Alt+F5**| EditorContextMenus.CodeWindow.Execute |
|Ir a vista|**Ctrl+M, Ctrl+G**| EditorContextMenus.CodeWindow.GoToView |
|Alternar archivo de encabezado/código|**Ctrl+K, Ctrl+O** (letra "O")| EditorContextMenus.CodeWindow.ToggleHeaderCodeFile |
|Visualización de la jerarquía de llamadas|**Ctrl+K, Ctrl+T**<br /><br /> o<br /><br /> **Ctrl+K, T**| EditorContextMenus.CodeWindow.ViewCallHierarchy |

### <a name="file"></a><a name="bkmk_file"></a> Archivo

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Salir|**Alt+F4**| File.Exit |
|Nuevo archivo|**Ctrl+N**| File.NewFile |
|Nuevo proyecto|**Ctrl+Mayús+N**| File.NewProject |
|Nuevo sitio web|**Mayús+Alt+N**| File.NewWebSite |
|Abrir archivo|**Ctrl+O** (letra "O")| File.OpenFile |
|Abrir el proyecto|**Ctrl+Mayús+O** (letra "O")| File.OpenProject |
|Abrir sitio web|**Mayús+Alt+O** (letra "O")| File.OpenWebSite |
|Impresión|**Ctrl+P**| File.Print |
|Guardar todo|**Ctrl+Mayús+S**| File.SaveAll |
|Guardar elementos seleccionados|**Ctrl+S**| File.SaveSelectedItems |
|Visualización en un explorador|**Ctrl+Mayús+W**| File.ViewinBrowser |

### <a name="help"></a><a name="bkmk_help"></a> Ayuda

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Agregar y quitar contenido de la Ayuda|**Ctrl+Alt+F1**| Help.AddandRemoveHelpContent |
|ayuda F1|**F1**| Help.F1Help |
|Ver la Ayuda|**Ctrl+F1**| Help.ViewHelp |
|Ayuda de la ventana|**Mayús+F1**| Help.WindowHelp |

### <a name="load-test"></a><a name="bkmk_loadtest"></a> Prueba de carga

|Comando|Método abreviado de teclado|Identificador de comando|
|-|-|-|
|Cambiar al panel Contador|**Ctrl+R, Q**| LoadTest.JumpToCounterPane |

### <a name="other-context-menus"></a><a name="bkmk_otherContext"></a> Otros menús contextuales

|Comando|Método abreviado de teclado|Identificador de comando|
|-|-|-|
|Agregar nuevo diagrama|**Insertar**| OtherContextMenus.MicrosoftDataEntityDesignContext.AddNewDiagram |

### <a name="project"></a><a name="bkmk_project"></a> Proyecto

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Agregar elemento existente|**Mayús+Alt+A**| Project.AddExistingItem |
|Agregar un nuevo elemento|**Ctrl+Mayús+A**| Project.AddNewItem |
|Asistente para clases|**Ctrl+Mayús+X**| Project.ClassWizard |
|Invalidar|**Ctrl+Alt+Insert**| Project.Override |
|Vista previa de los cambios|**Alt+** , luego **Alt+C**| Project.Previewchanges |
|Publicar los archivos seleccionados|**Alt+** , luego **Alt+P**| Project.Publishselectedfiles |
|Reemplazar los archivos seleccionados del servidor|**Alt+** , luego **Alt+R**| Project.Replaceselectedfilesfromserver |

### <a name="project-and-solution-context-menus"></a><a name="bkmk_projectContext"></a> Menús contextuales de proyectos y soluciones

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Bajar|**Alt+Flecha abajo**| ProjectandSolutionContextMenus.Item.MoveDown |
|Subir|**Alt+Flecha arriba**| ProjectandSolutionContextMenus.Item.MoveUp |

### <a name="refactor"></a><a name="bkmk_refactor"></a> Refactorizar

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Encapsular campo|**Ctrl+R, Ctrl+E**| Refactor.EncapsulateField |
|Extraer interfaz|**Ctrl+R, Ctrl+I**| Refactor.ExtractInterface |
|Extraer método|**Ctrl+R, Ctrl+M**| Refactor.ExtractMethod |
|Quitar parámetros|**Ctrl+R, Ctrl+V**| Refactor.RemoveParameters |
|Cambiar nombre|**Ctrl+R, Ctrl+R**| Refactor.Rename |
|Reordenar parámetros|**Ctrl+R, Ctrl+O** (letra "O")| Refactor.ReorderParameters |

### <a name="solution-explorer"></a><a name="bkmk_solutionexplorerGLOBAL"></a> Explorador de soluciones

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Filtro Archivos abiertos|**Ctrl+[** , **O** (letra "O")<br /><br /> o<br /><br /> **Ctrl+[** , **Ctrl+O** (letra "O")| SolutionExplorer.OpenFilesFilter |
|Filtro Cambios pendientes|**Ctrl+[** , **P**<br /><br /> o<br /><br /> **Ctrl+[** , **Ctrl+P**| SolutionExplorer.PendingChangesFilter |
|Sincronizar con el documento activo|**Ctrl+[** , **S**<br /><br /> o<br /><br /> **Ctrl+[** , **Ctrl+S**| SolutionExplorer.SyncWithActiveDocument |

### <a name="team"></a><a name="bkmk_team"></a> Equipo

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Ir a las ramas de Git|**Ctrl+0** (cero), **Ctrl+N**<br /><br /> o<br /><br /> **Ctrl+0, N**| Team.Git.GoToGitBranches |
|Ir a Cambios de GIT|**Ctrl+0** (cero), **Ctrl+G**<br /><br /> o<br /><br /> **Ctrl+0, G**| Team.Git.GoToGitChanges |
|Ir a confirmaciones de Git|**Ctrl+0** (cero), **Ctrl+O** (letra "O")<br /><br /> o<br /><br /> **Ctrl+0, O**| Team.Git.GoToGitCommits |
|Búsqueda de Team Explorer|**Ctrl+'**| Team.TeamExplorerSearch |

### <a name="team-foundation-context-menus"></a><a name="bkmk_TFcontext"></a> Menús contextuales de Team Foundation

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Ir a Compilaciones|**Ctrl+0** (cero), **Ctrl+B**<br /><br /> o<br /><br /> **Ctrl+0, B**| TeamFoundationContextMenus.Commands.GoToBuilds |
|Ir a Conectar|**Ctrl+0** (cero), **Ctrl+C**<br /><br /> o<br /><br /> **Ctrl+0, C**| TeamFoundationContextMenus.Commands.GoToConnect |
|Ir a Documentos|**Ctrl+0** (cero), **Ctrl+D**<br /><br /> o<br /><br /> **Ctrl+0, D**| TeamFoundationContextMenus.Commands.GoToDocuments |
|Ir a Página principal|**Ctrl+0** (cero), **Ctrl+H**<br /><br /> o<br /><br /> **Ctrl+0, H**| TeamFoundationContextMenus.Commands.GoToHome |
|Ir a Mi trabajo|**Ctrl+0** (cero), **Ctrl+M**<br /><br /> o<br /><br /> **Ctrl+0, M**| TeamFoundationContextMenus.Commands.GoToMyWork |
|Ir a Cambios pendientes|**Ctrl+0** (cero), **Ctrl+P**<br /><br /> o<br /><br /> **Ctrl+0, P**| TeamFoundationContextMenus.Commands.GoToPendingChanges |
|Ir a Informes|**Ctrl+0** (cero), **Ctrl+R**<br /><br /> o<br /><br /> **Ctrl+0, R**| TeamFoundationContextMenus.Commands.GoToReports |
|Ir a Configuración|**Ctrl+0** (cero), **Ctrl+S**<br /><br /> o<br /><br /> **Ctrl+0, S**| TeamFoundationContextMenus.Commands.GoToSettings |
|Ir a Web Access|**Ctrl+0** (cero), **Ctrl+A**<br /><br /> o<br /><br /> **Ctrl+0, S**| TeamFoundationContextMenus.Commands.GoToWebAccess |
|Ir a Elementos de trabajo|**Ctrl+0** (cero), **Ctrl+W**<br /><br /> o<br /><br /> **Ctrl+0, W**| TeamFoundationContextMenus.Commands.GoToWorkItems |

### <a name="test"></a><a name="bkmk_test"></a> Prueba

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Usar generador de pruebas automatizadas de IU|**Ctrl+\\, Ctrl+C**| Test.UseCodedUITestBuilder |
|Usar grabación de acciones existente|**Ctrl+\\, Ctrl+A**| Test.UseExistingActionRecording |

### <a name="test-explorer"></a><a name="bkmk_testexplorerGLOBAL"></a> Explorador de pruebas

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Depurar todas las pruebas|**Ctrl+R, Ctrl+A**| TestExplorer.DebugAllTests |
|Depurar todas las pruebas en contexto|**Ctrl+R, Ctrl+T**| TestExplorer.DebugAllTestsInContext |
|Depurar última ejecución|**Ctrl+R, D**| TestExplorer.DebugLastRun |
|Repetir la última ejecución|**Ctrl+R, L**| TestExplorer.RepeatLastRun |
|Ejecutar todas las pruebas|**Ctrl+R, A**| TestExplorer.RunAllTests |
|Ejecutar todas las pruebas en contexto|**Ctrl+R, T**| TestExplorer.RunAllTestsInContext |
|Mostrar Explorador de pruebas|**Ctrl+E, T**| TestExplorer.ShowTestExplorer |
|Abrir pestaña|**Ctrl+E, L**| LiveUnitTesting.OpenTab |
|Resultados de la cobertura de código|**Ctrl+E, C**| Test.CodeCoverageResults |

### <a name="tools"></a><a name="bkmk_tools"></a> Herramientas

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Asociar al proceso|**Ctrl+Alt+P**| Tools.AttachtoProcess |
|Administrador de fragmentos de código|**Ctrl+K, Ctrl+B**| Tools.CodeSnippetsManager |
|Forzar GC|**Ctrl+Mayús+Alt+F12, Ctrl+Mayús+Alt+F12**| Tools.ForceGC |

### <a name="view"></a><a name="bkmk_view"></a> Vista

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Todas las ventanas|**Mayús+Alt+M**| View.AllWindows |
|Explorador de arquitectura|**Ctrl+\\, Ctrl+R**| View.ArchitectureExplorer |
|atrás|**Alt+flecha izquierda** (funciona de manera diferente de View.NavigateBackward en el Editor de texto)| View.Backward |
|Ventana Marcador|**Ctrl+K, Ctrl+W**| View.BookmarkWindow |
|Examinar siguiente|**Ctrl+Mayús+1**| View.BrowseNext |
|Examinar anterior|**Ctrl+Mayús+2**| View.BrowsePrevious |
|Jerarquía de llamadas|**Ctrl+Alt+K**| View.CallHierarchy |
|Vista de clases|**Ctrl+Mayús+C**| View.ClassView |
|Cuadro combinado Ir a Búsqueda de Vista de clases|**Ctrl+K, Ctrl+V**| View.ClassViewGoToSearchCombo |
|Ventana Definición de código|**Ctrl+\\, D**<br /><br /> o<br /><br /> **Ctrl+\\, Ctrl+D**| View.CodeDefinitionWindow |
|Ventana Comandos|**Ctrl+Alt+A**| View.CommandWindow |
|Orígenes de datos|**Mayús+Alt+D**| View.DataSources |
|Esquema del documento|**Ctrl+Alt+T**| View.DocumentOutline |
|Editar etiqueta|**F2**| View.EditLabel |
|Lista de errores|**Ctrl+\\, E**<br /><br /> o<br /><br /> **Ctrl+\\, Ctrl+E**| View.ErrorList |
|F# Interactive|**Ctrl+Alt+F**| View.F#Interactive |
|Resultados de la búsqueda de símbolos|**Ctrl+Alt+F12**| View.FindSymbolResults |
|Adelante|**Alt+flecha derecha** (funciona de manera diferente de View.NavigateForward en el Editor de texto)| View.Forward |
|Reenviar el contexto de la navegación|**Ctrl+Mayús+7**| View.ForwardBrowseContext |
|Pantalla completa|**Mayús+Alt+Entrar**| View.FullScreen |
|Navegar hacia atrás|**Ctrl+-**| View.NavigateBackward |
|Navegar hacia adelante|**Ctrl+Mayús+-**| View.NavigateForward |
|Error siguiente|**Ctrl+Mayús+F12**| View.NextError |
|Notificaciones|**Ctrl+W, N**<br /><br /> o<br /><br /> **Ctrl+W, Ctrl+N**| View.Notifications |
|Explorador de objetos|**Ctrl+Alt+J**| View.ObjectBrowser |
|Cuadro combinado Ir a Búsqueda del Explorador de objetos|**Ctrl+K, Ctrl+R**| View.ObjectBrowserGoToSearchCombo |
|Output|**Ctrl+Alt+O** (letra "O")| View.Output |
|Menú contextual desplegable Examinar|**Ctrl+Mayús+8** (solo C++)| View.PopBrowseContext |
|Propiedades (ventana)|**F4**| View.PropertiesWindow |
|páginas de propiedades|**Mayús+F4**| View.PropertyPages |
|Vista de recursos|**Ctrl+Mayús+E**| View.ResourceView |
|Explorador de servidores|**Ctrl+Alt+S**| View.ServerExplorer |
|Mostrar etiqueta inteligente|**Mayús+Alt+F10**<br /><br /> o<br /><br /> **Ctrl+.**| View.ShowSmartTag |
|Explorador de soluciones|**Ctrl+Alt+L**| View.SolutionExplorer |
|Explorador de objetos de SQL Server|**Ctrl+\\, Ctrl+S**| View.SQLServerObjectExplorer |
|Lista de tareas|**Ctrl+\\, T**<br /><br /> o<br /><br /> **Ctrl+\\, Ctrl+T**| View.TaskList |
|Team Explorer de TFS|**Ctrl+\\, Ctrl+M**| View.TfsTeamExplorer |
|Cuadro de herramientas|**Ctrl+Alt+X**| View.Toolbox |
|Explorador de modelos UML|**Ctrl+\\, Ctrl+U**| View.UMLModelExplorer |
|Ver código|**F7**| View.ViewCode |
|Diseñador de vistas|**Mayús+F7**| View.ViewDesigner |
|Explorador web|**Ctrl+Alt+R**| View.WebBrowser |
|Acercamiento|**Ctrl+Mayús+,**| View.ZoomIn |
|Alejamiento|**Ctrl+Mayús+,**| View.ZoomOut |
|Mostrar Explorador de pruebas|**Ctrl+E, T**| TestExplorer.ShowTestExplorer |

### <a name="window"></a><a name="bkmk_window"></a> Ventana

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Activar ventana de documento|**Esc**| Window.ActivateDocumentWindow |
|Agregar pestaña a la selección|**Ctrl+Mayús+Alt+Barra espaciadora**| Window.AddTabtoSelection |
|Cerrar la ventana de documento|**Ctrl+F4**| Window.CloseDocumentWindow |
|Cerrar ventana de herramientas|**Mayús+Esc**| Window.CloseToolWindow |
|Mantener pestaña abierta|**Ctrl+Alt+Inicio**| Window.KeepTabOpen |
|Mover a la barra de navegación|**Ctrl+F2**| Window.MovetoNavigationBar |
|Ventana de documento siguiente|**Ctrl+F6**| Window.NextDocumentWindow |
|Ir a ventana de documento siguiente|**Ctrl+Tab**| Window.NextDocumentWindowNav |
|Panel siguiente|**Alt+F6**| Window.NextPane |
|Panel de división siguiente|**F6**| Window.NextSplitPane |
|Pestaña siguiente|**Ctrl+Alt+AvPág**<br /><br /> o<br /><br /> **Ctrl+PgDn**| Window.NextTab |
|Siguiente pestaña y agregar a la selección|**Ctrl+Mayús+Alt+AvPág**| Window.NextTabandAddtoSelection |
|Ir a ventana de herramientas siguiente|**Alt+F7**| Window.NextToolWindowNav |
|Ventana de documento anterior|**Ctrl+Mayús+F6**| Window.PreviousDocumentWindow |
|Ir a ventana de documento anterior|**Ctrl+Mayús+Tab**| Window.PreviousDocumentWindowNav |
|Panel anterior|**Mayús+Alt+F6**| Window.PreviousPane |
|Panel dividido anterior|**Mayús+F6**| Window.PreviousSplitPane |
|Pestaña anterior|**Ctrl+Alt+RePág**<br /><br /> o<br /><br /> **Ctrl+RePág**| Window.PreviousTab |
|Pestaña anterior y agregar a la selección|**Ctrl+Mayús+Alt+RePág**| Window.PreviousTabandAddtoSelection |
|Ir a ventana de herramientas anterior|**Mayús+Alt+F7**| Window.PreviousToolWindowNav |
|Inicio rápido|**Ctrl+Q**| Window.QuickLaunch |
|Categoría anterior de inicio rápido|**Ctrl+Mayús+Q**| Window.QuickLaunchPreviousCategory |
|Mostrar menú Acoplar|**Alt+-**| Window.ShowDockMenu |
|Mostrar lista de archivos Ex MDI|**Ctrl+Alt+Flecha abajo**| Window.ShowEzMDIFileList |
|Buscar en el Explorador de soluciones|**Ctrl+;**| Window.SolutionExplorerSearch |
|Buscar ventana|**Alt+`**| Window.WindowSearch |

### <a name="azure"></a><a name="bkmk_windowsazure"></a> Azure

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Reintentar la operación de script de servicio móvil|**Ctrl+Núm \*, Ctrl+R**| WindowsAzure.RetryMobileServiceScriptOperation |
|Mostrar detalles de error de script de servicio móvil|**Ctrl+Núm \*, Ctrl+D**| WindowsAzure.ShowMobileServiceScriptErrorDetails |

## <a name="context-specific-shortcuts"></a>Métodos abreviados de teclado específicos del contexto


### <a name="adonet-entity-data-model-designer"></a>ADO.NET Entity Data Model Designer

Los métodos abreviados de teclado específicos de este contexto son los siguientes:

|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Bajar|**Alt+Flecha abajo**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down |
|Abajo 5|**Alt+AvPág**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down5 |
|Hacia la parte inferior|**Alt+Fin**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToBottom |
|Hacia la parte superior|**Alt+Inicio**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToTop |
|Arriba|**Alt+Flecha arriba**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up |
|Arriba 5|**Alt+RePág**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up5 |
|Cambiar nombre|**Ctrl+R, R**| OtherContextMenus.MicrosoftDataEntityDesignContext.Refactor.Rename |
|Quitar del diagrama|**Mayús+Supr**| OtherContextMenus.MicrosoftDataEntityDesignContext.RemovefromDiagram |
|Explorador de Entity Data Model|**Ctrl+1**| View.EntityDataModelBrowser |
|Detalles de la asignación de Entity Data Model|**Ctrl+2**| View.EntityDataModelMappingDetails |

### <a name="class-diagram"></a>Diagrama de clases

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Contraer|**Núm -**| ClassDiagram.Collapse |
|Expanda|**Núm +**| ClassDiagram.Expand |
|Eliminar|**Ctrl+Supr**| Edit.Delete |
|Expandir o contraer la lista de tipo base|**Mayús+Alt+B**| Edit.ExpandCollapseBaseTypeList |
|Navegar al círculo|**Mayús+Alt+L**| Edit.NavigateToLollipop |
|Quitar del diagrama|**Eliminar**| Edit.RemovefromDiagram |
|Ver código|**Entrar**| View.ViewCode |

### <a name="coded-ui-test-editor"></a>Editor de pruebas de IU codificadas

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Copiar referencia al Portapapeles|**Ctrl+C**| OtherContextMenus.UITestEditorContextMenu.CopyReferencetoClipboard |
|Insertar retraso antes|**Ctrl+Alt+D**| OtherContextMenus.UITestEditorContextMenu.InsertDelayBefore |
|Buscar todo|**Mayús+Alt+L**| OtherContextMenus.UITestEditorContextMenu.LocateAll |
|Buscar control de IU|**Ctrl+Mayús+L**| OtherContextMenus.UITestEditorContextMenu.LocatetheUIControl |
|Mover código|**Ctrl+Alt+C**| OtherContextMenus.UITestEditorContextMenu.Movecode |
|Dividir en un nuevo método|**Ctrl+Mayús+T**| OtherContextMenus.UITestEditorContextMenu.Splitintoanewmethod |

### <a name="dataset-editor"></a>Editor de DataSet

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Insertar columna|**Insertar**| OtherContextMenus.ColumnContext.InsertColumn |
|Columna|**Ctrl+L**| OtherContextMenus.DbTableContext.Add.Column |

### <a name="difference-viewer"></a>Visor de diferencias

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Omitir espacio en blanco final|**Ctrl+\\, Ctrl+Barra espaciadora**| Diff.IgnoreTrimWhitespace |
|Vista alineada|**Ctrl+\\, Ctrl+1**| Diff.InlineView |
|Vista Solo izquierda|**Ctrl+\\, Ctrl+3**| Diff.LeftOnlyView |
|Diferencia siguiente|**F8**| Diff.NextDifference |
|Diferencia anterior|**Mayús+F8**| Diff.PreviousDifference |
|Vista Solo derecha|**Ctrl+\\, Ctrl+4**| Diff.RightOnlyView |
|Vista en paralelo|**Ctrl+\\, Ctrl+2**| Diff.SideBySideView |
|Cambiar entre las vistas izquierda y derecha|**Ctrl+\\, Ctrl+Tab**| Diff.SwitchBetweenLeftAndRight |
|Botón de alternancia Sincronizar vista|**Ctrl+\\, Ctrl+Flecha abajo**| Diff.SynchronizeViewToggle |
|Agregar comentario|**Ctrl+Mayús+K**| EditorContextMenus.CodeWindow.AddComment |
|Editar archivo local|**Ctrl+Mayús+P**| EditorContextMenus.CodeWindow.EditLocalFile |

### <a name="dom-explorer"></a>Explorador de DOM

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Actualizar|**F5**| DOMExplorer.Refresh |
|Seleccionar elemento|**Ctrl+B**| DOMExplorer.SelectElement |
|Mostrar diseño|**Ctrl+Mayús+I**| DOMExplorer.ShowLayout |

### <a name="f-interactive"></a>F# Interactive

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comando|Método abreviado de teclado|Identificador de comando|
|-|-|-|
|Cancelar evaluación interactiva|**Ctrl+Inter**| OtherContextMenus.FSIConsoleContext.CancelInteractiveEvaluation |

### <a name="graph-document-editor"></a>Editor de documentos de gráfico

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Agregar nodo|**Insertar**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Add.AddNode |
|Ambas dependencias|**B**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.BothDependencies |
|Dependencias entrantes|**I**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.IncomingDependencies |
|Dependencias salientes|**O**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.OutgoingDependencies |
|Nuevo comentario|**Ctrl+Mayús+K**<br /><br /> o<br /><br /> **Ctrl+E, C**| ArchitectureContextMenus.DirectedGraphContextMenu.NewComment |
|Quitar|**Eliminar**| ArchitectureContextMenus.DirectedGraphContextMenu.Remove |
|Cambiar nombre|**F2**| ArchitectureContextMenus.DirectedGraphContextMenu.Rename |

### <a name="graphics-diagnostics"></a>Diagnóstico de gráficos

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Capturar fotograma|None| Debug.Graphics.CaptureFrame |
|Bajar selección de píxeles|**Mayús+Alt+Flecha abajo**| Graphics.MovePixelSelectionDown |
|Mover selección de píxeles a la izquierda|**Mayús+Alt+Flecha izquierda**| Graphics.MovePixelSelectionLeft |
|Mover selección de píxeles a la derecha|**Mayús+Alt+Flecha derecha**| Graphics.MovePixelSelectionRight |
|Subir selección de píxeles|**Mayús+Alt+Flecha arriba**| Graphics.MovePixelSelectionUp |
|Ajustar el zoom al tamaño real|**Mayús+Alt+0** (cero)| Graphics.ZoomToActualSize |
|Ajustar al tamaño de la ventana|**Mayús+Alt+9**| Graphics.ZoomToFitInWindow |
|Acercamiento|**Mayús+Alt+=**| Graphics.ZoomIn |
|Alejamiento|**Mayús+Alt+-**| Graphics.ZoomOut |

### <a name="html-editor"></a>Editor de HTML

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comando|Método abreviado de teclado|Identificador de comando|
|-|-|-|
|Ir al controlador|**Ctrl+M, Ctrl+G**| OtherContextMenus.HTMLContext.GoToController |

### <a name="html-editor-design-view"></a>Vista de diseño del editor de HTML

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Mover control hacia abajo|**Ctrl+Flecha abajo**| Edit.MoveControlDown |
|Mover control hacia arriba|**Ctrl+Flecha arriba**| Edit.MoveControlUp |
|Negrita|**Ctrl+B**| Format.Bold |
|Convertir en hipervínculo|**Ctrl+L**| Format.ConverttoHyperlink |
|Insertar marcador|**Ctrl+Mayús+L**| Format.InsertBookmark |
|Cursiva|**Ctrl+I**| Format.Italic |
|Subrayado|**Ctrl+U**| Format.Underline |
|Agregar página de contenido|**Ctrl+M, Ctrl+C**| Project.AddContentPage |
|Columna a la izquierda|**Ctrl+Alt+Flecha izquierda**| Table.ColumntotheLeft |
|Columna a la derecha|**Ctrl+Alt+Flecha derecha**| Table.ColumntotheRight |
|Fila arriba|**Ctrl+Alt+Flecha arriba**| Table.RowAbove |
|Fila abajo|**Ctrl+Alt+Flecha abajo**| Table.RowBelow |
|Controles no visuales de ASP.NET|**Ctrl+Mayús+N**| View.ASP.NETNonvisualControls |
|Editar página maestra|**Ctrl+M, Ctrl+M**| View.EditMaster |
|Vista siguiente|**Ctrl+PgDn**| View.NextView |
|Mostrar etiqueta inteligente|**Mayús+Alt+F10**| View.ShowSmartTag |
|Ver marcado|**Mayús+F7**| View.ViewMarkup |
|Pestaña anterior|**Ctrl+RePág**| Window.PreviousTab |

### <a name="html-editor-source-view"></a>Vista de código fuente del editor de HTML

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Ir al controlador|**Ctrl+M, Ctrl+G**| OtherContextMenus.HTMLContext.GoToController |
|Vista siguiente|**Ctrl+PgDn**| View.NextView |
|Sincronizar vistas|**Ctrl+Mayús+Y**| View.SynchronizeViews |
|Diseñador de vistas|**Mayús+F7**| View.ViewDesigner |
|Pestaña anterior|**Ctrl+RePág**| Window.PreviousTab |

### <a name="layer-diagram"></a>Diagrama de capas

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comando|Método abreviado de teclado|Identificador de comando|
|-|-|-|
|Eliminar|**Mayús+Supr**| Edit.Delete |

### <a name="managed-resources-editor"></a>Editor de recursos administrados

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Editar celda|**F2**| Edit.EditCell |
|Quitar|**Eliminar**| Edit.Remove |
|Quitar fila|**Ctrl+Suprimir**| Edit.RemoveRow |
|Cancelar selección|**Escape**| Edit.SelectionCancel |
|Audio|**Ctrl+4**| Resources.Audio |
|Archivos|**Ctrl+5**| Resources.Files |
|Iconos|**Ctrl+3**| Resources.Icons |
|Imágenes|**Ctrl+2**| Resources.Images |
|Otros|**Ctrl+6**| Resources.Other |
|Cadenas|**Ctrl+1**| Resources.Strings |

### <a name="merge-editor-window"></a>Combinar ventana del editor

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Establecer foco en la ventana izquierda|**Alt+1**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonLeftWindow |
|Establecer foco en la ventana de resultados|**Alt+2**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonResultWindow |
|Establecer foco en la ventana derecha|**Alt+3**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonRightWindow |

### <a name="microsoft-sql-server-data-tools-schema-compare"></a>Herramientas de datos de Microsoft SQL Server, Comparación de esquemas

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Comparación de esquemas SSDT|**Mayús+Alt+C**| SQL.SSDTSchemaCompareCompare |
|Script de generación de comparación de esquemas SSDT|**Mayús+Alt+G**| SQL.SSDTSchemaCompareGenerateScript |
|Siguiente cambio de comparación de esquemas SSDT|**Mayús+Alt+.**| SQL.SSDTSchemaCompareNextChange |
|Cambio anterior de comparación de esquemas SSDT|**Mayús+Alt+,**| SQL.SSDTSchemaComparePreviousChange |
|Detener comparación de esquemas SSDT|**Alt+Inter**| SQL.SSDTSchemaCompareStop |
|Actualizaciones de escritura de comparación de esquemas SSDT|**Mayús+Alt+U**| SQL.SSDTSchemaCompareWriteUpdates |

### <a name="microsoft-sql-server-data-tools-table-designer"></a>Herramientas de datos de Microsoft SQL Server, Diseñador de tablas

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|CommitAllEdits|**Mayús+Alt+U**|
|Expandir caracteres comodín|**Ctrl+R, E**<br /><br /> o<br /><br /> **Ctrl+R, Ctrl+E**| SQL.ExpandWildcards |
|Nombres completos|**Ctrl+R, Q**<br /><br /> o<br /><br /> **Ctrl+R, Ctrl+Q**| SQL.FullyqualifyNames |
|Mover a esquema|**Ctrl+R, M**<br /><br /> o<br /><br /> **Ctrl+R, Ctrl+M**| SQL.MovetoSchema |
|Cambiar nombre|**F2**<br /><br /> o<br /><br /> **Ctrl+R, R**<br /><br /> o<br /><br /> **Ctrl+R, Ctrl+R**| SQL.Rename |
|ViewFileInScriptPanel|**Mayús+Alt+AvPág**| |

### <a name="microsoft-sql-server-data-tools-t-sql-editor"></a>Herramientas de datos de Microsoft SQL Server, Editor de T-SQL

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|CommitAllEdits|**Mayús+Alt+U**|
|Ejecutar con depurador|**Alt+F5**| SQL.ExecuteWithDebugger |
|Expandir caracteres comodín|**Ctrl+R, E**<br /><br /> o<br /><br /> **Ctrl+R, Ctrl+E**| SQL.ExpandWildcards |
|Nombres completos|**Ctrl+R, Q**<br /><br /> o<br /><br /> **Ctrl+R, Ctrl+Q**| SQL.FullyqualifyNames |
|Mover a esquema|**Ctrl+R, M**<br /><br /> o<br /><br /> **Ctrl+R, Ctrl+M**| SQL.MovetoSchema |
|Cambiar nombre|**F2**<br /><br /> o<br /><br /> **Ctrl+R, R**<br /><br /> o<br /><br /> **Ctrl+R, Ctrl+R**| SQL.Rename |
|Editor de T SQL: Cancelar consulta|**Alt+Inter**| SQL.TSqlEditorCancelQuery |
|Editor de T SQL: Ejecutar consulta|**Ctrl+Mayús+E**| SQL.TSqlEditorExecuteQuery |
|Editor de T-SQL: Resultados como archivo|**Ctrl+D, F**| SQL.TSqlEditorResultsAsFile |
|Editor de T-SQL: Resultados como cuadrícula|**Ctrl+D, G**| SQL.TSqlEditorResultsAsGrid |
|Editor de T-SQL: Resultados como texto|**Ctrl+D, T**| SQL.TSqlEditorResultsAsText |
|Editor de T-SQL: Mostrar plan estimado|**Ctrl+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|Editor de T-SQL: Alternar plan de ejecución|**Ctrl+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|Editor de T-SQL: Alternar panel de resultados|**Ctrl+D, R**| SQL.TSqlEditorToggleResultsPane |
|Editor de T-SQL: Clonar consulta|**Ctrl+Alt+N**|SQL.TSqlEditorCloneQuery |
|Editor de T-SQL: Cuadro combinado base de datos|**Mayús+Alt+AvPág**|SQL.TSqlEditorDatabaseCombo |

### <a name="microsoft-sql-server-data-tools-t-sql-pdw-editor"></a>Herramientas de datos de Microsoft SQL Server, Editor PDW de T-SQL

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Editor de T SQL: Cancelar consulta|**Alt+Inter**| SQL.TSqlEditorCancelQuery |
|Editor de T SQL: Ejecutar consulta|**Ctrl+Mayús+E**| SQL.TSqlEditorExecuteQuery |
|Editor de T-SQL: Resultados como archivo|**Ctrl+D, F**| SQL.TSqlEditorResultsAsFile |
|Editor de T-SQL: Resultados como cuadrícula|**Ctrl+D, G**| SQL.TSqlEditorResultsAsGrid |
|Editor de T-SQL: Resultados como texto|**Ctrl+D, T**| SQL.TSqlEditorResultsAsText |
|Editor de T-SQL: Mostrar plan estimado|**Ctrl+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|Editor de T-SQL: Alternar plan de ejecución|**Ctrl+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|Editor de T-SQL: Alternar panel de resultados|**Ctrl+D, R**| SQL.TSqlEditorToggleResultsPane |
|Editor de T-SQL: Clonar consulta|**Ctrl+Alt+N**|SQL.TSqlEditorCloneQuery |
|Editor de T-SQL: Clonar consulta|**Mayús+Alt+AvPág**|SQL.TSqlEditorCloneQuery |

### <a name="page-inspector"></a>Inspector de página

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comando|Método abreviado de teclado|Identificador de comando|
|-|-|-|
|Minimizar|**F12**| PageInspector.Minimize |

### <a name="query-designer"></a>Diseñador de consultas

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Cancelar la recuperación de datos|**Ctrl+T**| QueryDesigner.CancelRetrievingData |
|Criterios|**Ctrl+2**| QueryDesigner.Criteria |
|Diagrama|**Ctrl+1**| QueryDesigner.Diagram |
|Ejecutar SQL|**Ctrl+R**| QueryDesigner.ExecuteSQL |
|Ir a fila|**Ctrl+G**| QueryDesigner.GotoRow |
|Modo de combinación|**Ctrl+Mayús+J**| QueryDesigner.JoinMode |
|Resultados|**Ctrl+4**| QueryDesigner.Results |
|Sql|**Ctrl+3**| QueryDesigner.SQL |

### <a name="query-results"></a>Resultados de la consulta

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Nueva fila de resultados de la consulta|**Alt+Fin**| SQL.QueryResultsNewRow |
|Actualizar resultados de la consulta|**Mayús+Alt+R**| SQL.QueryResultsRefresh |
|Detener resultados de la consulta|**Alt+Inter**| SQL.QueryResultsStop |

### <a name="report-designer"></a>Diseñador de informes

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Dividir línea|**Entrar**| Edit.BreakLine |
|Carácter a la izquierda|**Flecha izquierda**| Edit.CharLeft |
|Extender un carácter a la izquierda|**Mayús+Flecha izquierda**| Edit.CharLeftExtend |
|Carácter a la derecha|**Flecha derecha**| Edit.CharRight |
|Extender un carácter a la derecha|**Mayús+Flecha derecha**| Edit.CharRightExtend |
|Pestaña Insertar|**Tabulación**| Edit.InsertTab |
|Línea abajo|**Flecha abajo**| Edit.LineDown |
|Extender una línea abajo|**Mayús+Flecha abajo**| Edit.LineDownExtend |
|Línea arriba|**Flecha arriba**| Edit.LineUp |
|Extender una línea arriba|**Mayús+Flecha arriba**| Edit.LineUpExtend |
|Mover control hacia abajo|**Ctrl+Flecha abajo**| Edit.MoveControlDown |
|Mover el control a la izquierda|**Ctrl+Flecha izquierda**| Edit.MoveControlLeft |
|Mover el control a la derecha|**Ctrl+Flecha derecha**| Edit.MoveControlRight |
|Mover control hacia arriba|**Ctrl+Flecha arriba**| Edit.MoveControlUp |
|Cancelar selección|**Esc**| Edit.SelectionCancel |
|Ajustar tamaño de control por abajo|**Ctrl+Mayús+Flecha abajo**| Edit.SizeControlDown |
|Ajustar tamaño de control por la izquierda|**Ctrl+Mayús+Flecha izquierda**| Edit.SizeControlLeft |
|Ajustar tamaño de control por la derecha|**Ctrl+Mayús+Flecha derecha**| Edit.SizeControlRight |
|Ajustar tamaño de control por arriba|**Ctrl+Mayús+Flecha arriba**| Edit.SizeControlUp |
|Tabulación a la izquierda|**Mayús+Tab**| Edit.TabLeft |
|datos de informe|**Ctrl+Alt+D**| View.ReportData |

### <a name="sequence-diagram"></a>Diagrama de secuencia

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Navegar al código|**F12**| ArchitectureDesigner.Sequence.NavigateToCode |
|Eliminar|**Mayús+Supr**| Edit.Delete |

### <a name="settings-designer"></a>Diseñador de configuración

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Editar celda|**F2**| Edit.EditCell |
|Quitar fila|**Ctrl+Suprimir**| Edit.RemoveRow |
|Cancelar selección|**Esc**| Edit.SelectionCancel |
|Ver código|**F7**| View.ViewCode |

### <a name="solution-explorer"></a>Explorador de soluciones

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comando|Método abreviado de teclado|Identificador de comando|
|-|-|-|
|Ver en Inspector de páginas|**Ctrl+K, Ctrl+G**| ClassViewContextMenus.ClassViewProject.View.ViewinPageInspector |

### <a name="team-explorer"></a>Team Explorer

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comando|Método abreviado de teclado|Identificador de comando|
|-|-|-|
|Eliminar|**Eliminar**| Edit.Delete |
|Cambiar nombre|**F2**| File.Rename |
|Ir a Navegación de Team Explorer|**Alt+Inicio**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNavigation |
|Ir a Contenido de sección siguiente de Team Explorer|**Alt+Flecha abajo**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNextSectionContent |
|Ir a Contenido de página de Team Explorer|**Alt+0** (cero)| TeamFoundationContextMenus.Commands.GoToTeamExplorerPageContent |
|Ir a Contenido de sección anterior de Team Explorer|**Alt+Flecha arriba**| TeamFoundationContextMenus.Commands.GoToTeamExplorerPreviousSectionContent |
|Ir a Contenido de sección 1 de Team Explorer|**Alt+1**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection1Content |
|Ir a Contenido de sección 2 de Team Explorer|**Alt+2**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection2Content |
|Ir a Contenido de sección 3 de Team Explorer|**Alt+3**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection3Content |
|Ir a Contenido de sección 4 de Team Explorer|**Alt+4**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection4Content |
|Ir a Contenido de sección 5 de Team Explorer|**Alt+5**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection5Content |
|Ir a Contenido de sección 6 de Team Explorer|**Alt+6**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection6Content |
|Ir a Contenido de sección 7 de Team Explorer|**Alt+7**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection7Content |
|Ir a Contenido de sección 8 de Team Explorer|**Alt+8**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection8Content |
|Ir a Contenido de sección 9 de Team Explorer|**Alt+9**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection9Content |
|Navegar hacia atrás en Team Explorer|**Alt+Flecha izquierda**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateBackward |
|Navegar hacia delante en Team Explorer|**Alt+Flecha derecha**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateForward |
|Contexto de TFS: página Mi trabajo, Crear copia del elemento de trabajo|**Mayús+Alt+C**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageCreateCopyWI |
|Contexto de TFS: página Mi trabajo, Nuevo elemento de trabajo vinculado|**Mayús+Alt+L**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageNewLinkedWI |
|Actualizar|**F5**| View.Refresh |

### <a name="test-explorer"></a>Explorador de pruebas

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comando|Método abreviado de teclado|Identificador de comando|
|-|-|-|
|Abrir prueba|**F12**| TestExplorer.OpenTest |

### <a name="text-editor"></a>Editor de texto

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


| Comandos | Métodos abreviados de teclado |Identificador de comando|
|-|-|-|
|Dividir línea| **Entrar**<br /><br /> o<br /><br /> **Mayús+Entrar** | Edit.BreakLine |
|Carácter a la izquierda| **Flecha izquierda** | Edit.CharLeft |
|Extender un carácter a la izquierda| **Mayús+Flecha izquierda** | Edit.CharLeftExtend |
|Extender columna un carácter a la izquierda| **Mayús+Alt+Flecha izquierda** | Edit.CharLeftExtendColumn |
|Carácter a la derecha| **Flecha derecha** | Edit.CharRight |
|Extender un carácter a la derecha| **Mayús+Flecha derecha** | Edit.CharRightExtend |
|Extender columna un carácter a la derecha| **Mayús+Alt+Flecha derecha** | Edit.CharRightExtendColumn |
|Eliminar marcadores| **Ctrl+K, Ctrl+L** | Edit.ClearBookmarks |
|Contraer toda la esquematización| **Ctrl+M, Ctrl+A** | Edit.CollapseAllOutlining |
|Contraer región actual| **Ctrl+M, Ctrl+S** | Edit.CollapseCurrentRegion |
|Contraer etiqueta| **Ctrl+M, Ctrl+T** | Edit.CollapseTag |
|Contraer a definiciones| **Ctrl+M, Ctrl+O** (letra "O") | Edit.CollapseToDefinitions |
|Contraer selección| **Mayús+Alt+-** | Edit.ContractSelection |
|Comentar selección| **Ctrl+K, Ctrl+C** | Edit.CommentSelection |
|Completar palabra| **Ctrl+Barra espaciadora**<br /><br /> o<br /><br /> **Alt+Flecha derecha** | Edit.CompleteWord |
|Copiar sugerencia de parámetros| **Ctrl+Mayús+Alt+C** | Edit.CopyParameterTip |
|Reducir nivel de filtro| **Alt+,** | Edit.DecreaseFilterLevel |
|Eliminar hacia atrás| **Retroceso**<br /><br /> o<br /><br /> **Mayús+Retroceso** | Edit.DeleteBackwards |
|Eliminar espacio en blanco horizontal| **Ctrl+K, Ctrl+\\** | Edit.DeleteHorizontalWhiteSpace |
|Final del documento| **Ctrl+Fin** | Edit.DocumentEnd |
|Extender al final del documento| **Ctrl+Mayús+Fin** | Edit.DocumentEndExtend |
|Inicio de documento| **Ctrl+Inicio** | Edit.DocumentStart |
|Extender al inicio del documento| **Ctrl+Mayús+Inicio** | Edit.DocumentStartExtend |
|Expandir toda la esquematización| **Ctrl+M, Ctrl+X** | Edit.ExpandAllOutlining |
|Expandir región actual| **Ctrl+M, Ctrl+E** | Edit.ExpandCurrentRegion |
|Ampliar selección| **Mayús+Alt+=** | Edit.ExpandSelection |
|Expandir selección hasta el bloque contenedor| **Mayús+Alt+]** | Edit.ExpandSelectiontoContainingBlock |
|Aplicación de formato al documento| **Ctrl+K, Ctrl+D** | Edit.FormatDocument |
|Aplicación de formato a la selección| **Ctrl+K, Ctrl+F** | Edit.FormatSelection |
|Ir a todo| **Ctrl+T**<br /><br /> o<br /><br /> **Ctrl+,** | Edit.GotoAll |
|Ir a llave| **Ctrl+]** | Edit.GotoBrace |
|Extender e ir a llave| **Ctrl+Mayús+]** | Edit.GotoBraceExtend |
|Ir a archivos recientes| **Ctrl+T,R** | Edit.GotoRecent |
|Ir al siguiente problema del archivo| **Alt+AvPág** | Edit.GotoNextIssueinFile |
|Ir al problema anterior del archivo| **Alt+RePág** | Edit.GotoPreviousIssueinFile |
|Ocultar selección| **Ctrl+M, Ctrl+H** | Edit.HideSelection |
|Aumentar nivel de filtro| **Alt+.** | Edit.IncreaseFilterLevel |
|Búsqueda incremental| **Ctrl+I** | Edit.IncrementalSearch |
|Incluir símbolos de inserción en todas las coincidencias| **Mayús+Alt+;** | Edit.InsertCaretsatAllMatching |
|Incluir siguiente símbolo de inserción coincidente| **Mayús+Alt+.** | Edit.InsertNextMatchingCaret |
|Pestaña Insertar| **Tabulación** | Edit.InsertTab |
|Cortar línea| **Ctrl+L** | Edit.LineCut |
|Eliminar línea| **Ctrl+Mayús+L** | Edit.LineDelete |
|Línea abajo| **Flecha abajo** | Edit.LineDown |
|Extender una línea abajo| **Mayús+Flecha abajo** | Edit.LineDownExtend |
|Extender columna una línea abajo| **Mayús+Alt+Flecha abajo** | Edit.LineDownExtendColumn |
|Final de línea| **Fin** | Edit.LineEnd |
|Extender al final de la línea| **Mayús+Fin** | Edit.LineEndExtend |
|Extender columna al final de la línea| **Mayús+Alt+Fin** | Edit.LineEndExtendColumn |
|Abrir línea encima| **Ctrl+Entrar** | Edit.LineOpenAbove |
|Abrir línea debajo| **Ctrl+Mayús+Entrar** | Edit.LineOpenBelow |
|Inicio de línea| **Página principal** | Edit.LineStart |
|Extender al inicio de la línea| **Mayús+Inicio** | Edit.LineStartExtend |
|Extender columna al inicio de la línea| **Mayús+Alt+Inicio** | Edit.LineStartExtendColumn |
|Transponer línea| **Mayús+Alt+T** | Edit.LineTranspose |
|Línea arriba| **Flecha arriba** | Edit.LineUp |
|Extender una línea arriba| **Mayús+Flecha arriba** | Edit.LineUpExtend |
|Extender columna una línea arriba| **Mayús+Alt+Flecha arriba** | Edit.LineUpExtendColumn |
|Enumerar miembros| **Ctrl+J** | Edit.ListMembers |
|Poner en minúsculas| **Ctrl+U** | Edit.MakeLowercase |
|Poner en mayúsculas| **Ctrl+Mayús+U** | Edit.MakeUppercase |
|Bajar líneas seleccionadas| **Alt+Flecha abajo** | Edit.MoveSelectedLinesDown |
|Subir líneas seleccionadas| **Alt+Flecha arriba** | Edit.MoveSelectedLinesUp |
|Referencia resaltada siguiente| **Ctrl+Mayús+Flecha abajo** | Edit.NextHighlightedReference |
|Modo de reemplazo| **Insertar** | Edit.OvertypeMode |
|Página abajo| **AvPág** | Edit.PageDown |
|Extender una página abajo| **Mayús+AvPág** | Edit.PageDownExtend |
|Re Pág| **RePág** | Edit.PageUp |
|Extender una página arriba| **Mayús+RePág** | Edit.PageUpExtend |
|Información de parámetros| **Ctrl+Mayús+Barra espaciadora** | Edit.ParameterInfo |
|Pegar sugerencia de parámetros| **Ctrl+Mayús+Alt+P** | Edit.PasteParameterTip |
|Leer hacia atrás| **Ctrl+Alt+-** | Edit.PeekBackward |
|Ver la definición sin salir| **Alt+F12** | Edit.PeekDefinition |
|Leer hacia delante| **Ctrl+Alt+=** | Edit.PeekForward |
|Referencia resaltada anterior| **Ctrl+Mayús+Flecha arriba** | Edit.PreviousHighlightedReference |
|Información rápida| **Ctrl+K, Ctrl+I** | Edit.QuickInfo |
|Invertir búsqueda incremental| **Ctrl+Mayús+I** | Edit.ReverseIncrementalSearch |
|Desplazar línea hacia abajo| **Ctrl+Flecha abajo** | Edit.ScrollLineDown |
|Desplazar línea hacia arriba| **Ctrl+Flecha arriba** | Edit.ScrollLineUp |
|Seleccionar palabra actual| **Ctrl+W** | Edit.SelectCurrentWord |
|Cancelar selección| **Escape** | Edit.SelectionCancel |
|Seleccionar hasta último retroceso| **Ctrl+=** | Edit.SelectToLastGoBack |
|Mostrar menú CodeLens| **Ctrl+K, Ctrl+\`** | Edit.ShowCodeLensMenu |
|Mostrar el menú de navegación| **Alt+\`** | Edit.ShowNavigateMenu |
|Detener ocultar actual| **Ctrl+M, Ctrl+U** | Edit.StopHidingCurrent |
|Detener esquematización| **Ctrl+M, Ctrl+P** | Edit.StopOutlining |
|Cambiar delimitador| **Ctrl+K, Ctrl+A** | Edit.SwapAnchor |
|Tabulación a la izquierda| **Mayús+Tab** | Edit.TabLeft |
|Alternar toda la esquematización| **Ctrl+M, Ctrl+L** | Edit.ToggleAllOutlining |
|Alternar marcador| **Ctrl+K, Ctrl+K** | Edit.ToggleBookmark |
|Alternar el modo de finalización| **Ctrl+Alt+Barra espaciadora** | Edit.ToggleCompletionMode |
|Alternar expansión de esquematización| **Ctrl+M, Ctrl+M** | Edit.ToggleOutliningExpansion |
|Alternar acceso directo de la Lista de tareas| **Ctrl+K, Ctrl+H** | Edit.ToggleTaskListShortcut |
|Alternar ajuste de línea| **Ctrl+E, Ctrl+W** | Edit.ToggleWordWrap |
|Selección sin comentarios| **Ctrl+K, Ctrl+U** | Edit.UncommentSelection |
|Final de la vista| **Ctrl+PgDn** | Edit.ViewBottom |
|Extender al final de la vista| **Ctrl+Mayús+AvPág** | Edit.ViewBottomExtend |
|Principio de la vista| **Ctrl+RePág** | Edit.ViewTop |
|Extender al principio de la vista| **Ctrl+Mayús+RePág** | Edit.ViewTopExtend |
|Ver espacios en blanco| **Ctrl+R, Ctrl+W** | Edit.ViewWhiteSpace |
|Eliminar hasta el final de la palabra| **Ctrl+Suprimir** | Edit.WordDeleteToEnd |
|Eliminar hasta el principio de la palabra| **Ctrl+Retroceso** | Edit.WordDeleteToStart |
|Palabra siguiente| **Ctrl+Flecha derecha** | Edit.WordNext |
|Extender a la palabra siguiente| **Ctrl+Mayús+Flecha derecha** | Edit.WordNextExtend |
|Extender columna a la palabra siguiente| **Ctrl+Mayús+Alt+Flecha derecha** | Edit.WordNextExtendColumn |
|Palabra anterior| **Ctrl+Flecha izquierda** | Edit.WordPrevious |
|Extender a la palabra anterior| **Ctrl+Mayús+Flecha izquierda** | Edit.WordPreviousExtend |
|Extender columna a la palabra anterior| **Ctrl+Mayús+Alt+Flecha izquierda** | Edit.WordPreviousExtendColumn |
|Transponer palabra| **Ctrl+Mayús+T** | Edit.WordTranspose |
|Ejecutar en modo interactivo| **Alt+Entrar** | EditorContextMenus.CodeWindow.ExecuteInInteractive |
|Ejecutar línea en modo interactivo| **Alt+'** | EditorContextMenus.CodeWindow.ExecuteLineInInteractive |
|Ver en Inspector de páginas| **Ctrl+K, Ctrl+G** | OtherContextMenus.HTMLContext.ViewinPageInspector |
|TFS>Anotar>Mover>Región siguiente| **Alt+AvPág** | TeamFoundationContextMenus.Annotate.TfsAnnotateMoveNextRegion |
|TFS>Anotar>Mover>Región anterior| **Alt+RePág** | TeamFoundationContextMenus.Annotate.TfsAnnotateMovePreviousRegion |

### <a name="uml-activity-diagram"></a>Diagrama de actividades UML

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comando|Método abreviado de teclado|Identificador de comando|
|-|-|-|
|Eliminar|**Mayús+Supr**| Edit.Delete |

### <a name="uml-class-diagram"></a>Diagrama de clases de UML

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comando|Método abreviado de teclado|Identificador de comando|
|-|-|-|
|Eliminar del modelo|**Mayús+Supr**| Edit.DeleteFromModel |

### <a name="uml-component-diagram"></a>Diagrama de componentes UML

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comando|Método abreviado de teclado|Identificador de comando|
|-|-|-|
|Eliminar del modelo|**Mayús+Supr**| Edit.DeleteFromModel |

### <a name="uml-use-case-diagram"></a>Diagrama de casos de uso UML

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comando|Método abreviado de teclado|Identificador de comando|
|-|-|-|
|Eliminar del modelo|**Mayús+Supr**| Edit.DeleteFromModel |

### <a name="vc-accelerator-editor"></a>Editor de aceleradores VC

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Nuevo acelerador|**Insertar**| Edit.NewAccelerator |
|Tecla siguiente|**Ctrl+W**| Edit.NextKeyTyped |

### <a name="vc-dialog-editor"></a>Editor de cuadros de diálogo VC

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Mover control hacia abajo|**Flecha abajo**| Edit.MoveControlDown |
|Mover el control a la izquierda|**Flecha izquierda**| Edit.MoveControlLeft |
|Mover el control a la derecha|**Flecha derecha**| Edit.MoveControlRight |
|Mover control hacia arriba|**Flecha arriba**| Edit.MoveControlUp |
|Desplazar columna a la izquierda|**Ctrl+Flecha izquierda**| Edit.ScrollColumnLeft |
|Desplazar columna a la derecha|**Ctrl+Flecha derecha**| Edit.ScrollColumnRight |
|Desplazar línea hacia abajo|**Ctrl+Flecha abajo**| Edit.ScrollLineDown |
|Desplazar línea hacia arriba|**Ctrl+Flecha arriba**| Edit.ScrollLineUp |
|Ajustar tamaño de control por abajo|**Mayús+Flecha abajo**| Edit.SizeControlDown |
|Ajustar tamaño de control por la izquierda|**Mayús+Flecha izquierda**| Edit.SizeControlLeft |
|Ajustar tamaño de control por la derecha|**Mayús+Flecha derecha**| Edit.SizeControlRight |
|Ajustar tamaño de control por arriba|**Mayús+Flecha arriba**| Edit.SizeControlUp |
|Alinear lados inferiores|**Ctrl+Mayús+Flecha abajo**| Format.AlignBottoms |
|Alinear centros|**Mayús+F9**| Format.AlignCenters |
|Alinear lados izquierdos|**Ctrl+Mayús+Flecha izquierda**| Format.AlignLefts |
|Alinear puntos medios|**F9**| Format.AlignMiddles |
|Alinear lados derechos|**Ctrl+Mayús+Flecha derecha**| Format.AlignRights |
|Alinear lados superiores|**Ctrl+Mayús+Flecha arriba**| Format.AlignTops |
|Botón Inferior|**Ctrl+B**| Format.ButtonBottom |
|Botón Derecha|**Ctrl+R**| Format.ButtonRight |
|Centrar horizontalmente|**Ctrl+Mayús+F9**| Format.CenterHorizontal |
|Centrar verticalmente|**Ctrl+F9**| Format.CenterVertical |
|Comprobar teclas de acceso|**Ctrl+M**| Format.CheckMnemonics |
|Ajustar al contenido|**Mayús+F7**| Format.SizetoContent |
|Espaciar horizontalmente|**Alt+Flecha derecha**<br /><br /> o<br /><br /> **Alt+Flecha izquierda**| Format.SpaceAcross |
|Espaciar verticalmente|**Alt+Flecha arriba**<br /><br /> o<br /><br /> **Alt+Flecha abajo**| Format.SpaceDown |
|Orden de tabulación|**Ctrl+D**| Format.TabOrder |
|Probar cuadro de diálogo|**Ctrl+T**| Format.TestDialog |
|Alternar guías|**Ctrl+G**| Format.ToggleGuides |

### <a name="vc-image-editor"></a>Editor de imágenes VC

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Herramienta Aerógrafo|**Ctrl+A**| Image.AirbrushTool |
|Herramientas Pincel|**Ctrl+B**| Image.BrushTool |
|Copiar y resaltar selección|**Ctrl+Mayús+U**| Image.CopyandOutlineSelection |
|Dibujar figuras opacas|**Ctrl+J**| Image.DrawOpaque |
|Herramienta Elipse|**Alt+P**| Image.EllipseTool |
|Herramienta Borrar|**Ctrl+Mayús+I**| Image.EraseTool |
|Herramienta Elipse con relleno|**Ctrl+Mayús+Alt+P**| Image.FilledEllipseTool |
|Herramienta Rectángulo con relleno|**Ctrl+Mayús+Alt+R**| Image.FilledRectangleTool |
|Herramienta Rectángulo redondeado con relleno|**Ctrl+Mayús+Alt+W**| Image.FilledRoundedRectangleTool |
|Rellenar (herramienta)|**Ctrl+F**| Image.FillTool |
|Voltear horizontalmente|**Ctrl+H**| Image.FlipHorizontal |
|Voltear verticalmente|**Mayús+Alt+H**| Image.FlipVertical |
|Pincel más grande|**Ctrl+=**| Image.LargerBrush |
|Herramienta Línea|**Ctrl+L**| Image.LineTool |
|Herramienta Aumento|**Ctrl+M**| Image.MagnificationTool |
|Aumento|**Ctrl+Mayús+M**| Image.Magnify |
|Nuevo tipo de imagen|**Insertar**| Image.NewImageType |
|Color siguiente|**Ctrl+]**<br /><br /> o<br /><br /> **Ctrl+Flecha derecha**| Image.NextColor |
|Color a la derecha siguiente|**Ctrl+Mayús+]**<br /><br /> o<br /><br /> **Ctrl+Mayús+Flecha derecha**| Image.NextRightColor |
|Herramienta Elipse con contorno|**Mayús+Alt+P**| Image.OutlinedEllipseTool |
|Herramienta Rectángulo con contorno|**Mayús+Alt+R**| Image.OutlinedRoundRectangleTool |
|Herramienta Rectángulo redondeado con contorno|**Mayús+Alt+W**| Image.OutlinedRoundedRectangleTool |
|Herramienta Lápiz|**Ctrl+I**| Image.PencilTool |
|Color anterior|**Ctrl+[**<br /><br /> o<br /><br /> **Ctrl+Flecha izquierda**| Image.PreviousColor |
|Color a la derecha anterior|**Ctrl+Mayús+[**<br /><br /> o<br /><br /> **Ctrl+Mayús+Flecha izquierda**| Image.PreviousRightColor |
|Herramienta Seleccionar rectángulo|**Mayús+Alt+S**| Image.RectangleSelectionTool |
|Herramienta Rectángulo|**Alt+R**| Image.RectangleTool |
|Girar 90 grados|**Ctrl+Mayús+H**| Image.Rotate90Degrees |
|Herramienta Rectángulo redondeado|**Alt+W**| Image.RoundedRectangleTool |
|Mostrar cuadrícula|**Ctrl+Alt+S**| Image.ShowGrid |
|Mostrar cuadrícula de mosaico|**Ctrl+Mayús+Alt+S**| Image.ShowTileGrid |
|Pincel pequeño|**Ctrl+.**| Image.SmallBrush |
|Pincel más pequeño|**Ctrl+-**| Image.SmallBrush |
|Herramienta Texto|**Ctrl+T**| Image.TextTool |
|Usar la selección como pincel|**Ctrl+U**| Image.UseSelectionasBrush |
|Acercamiento|**Ctrl+Mayús+,**<br /><br /> o<br /><br /> **Ctrl+Flecha arriba**| Image.ZoomIn |
|Alejamiento|**Ctrl+Mayús+,**<br /><br /> o<br /><br /> **Ctrl+Flecha abajo**| Image.ZoomOut |

### <a name="vc-string-editor"></a>Editor de cadenas VC

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comando|Método abreviado de teclado|Identificador de comando|
|-|-|-|
|cadena nueva|**Insertar**| Edit.NewString |

### <a name="view-designer"></a>Diseñador de vistas

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Cancelar la recuperación de datos|**Ctrl+T**| QueryDesigner.CancelRetrievingData |
|Criterios|**Ctrl+2**| QueryDesigner.Criteria |
|Diagrama|**Ctrl+1**| QueryDesigner.Diagram |
|Ejecutar SQL|**Ctrl+R**| QueryDesigner.ExecuteSQL |
|Ir a fila|**Ctrl+G**| QueryDesigner.GotoRow |
|Modo de combinación|**Ctrl+Mayús+J**| QueryDesigner.JoinMode |
|Resultados|**Ctrl+4**| QueryDesigner.Results |
|Sql|**Ctrl+3**| QueryDesigner.SQL |

### <a name="visual-studio"></a>Programa para la mejora

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comando|Método abreviado de teclado|Identificador de comando|
|-|-|-|
|Ocultar panel Métodos|**Ctrl+1**| OtherContextMenus.ORDesignerContext.HideMethodsPane |

### <a name="windows-forms-designer"></a>Diseñador de Windows Forms

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Dividir línea|**Entrar**| Edit.BreakLine |
|Carácter a la izquierda|**Flecha izquierda**| Edit.CharLeft |
|Extender un carácter a la izquierda|**Mayús+Flecha izquierda**| Edit.CharLeftExtend |
|Carácter a la derecha|**Flecha derecha**| Edit.CharRight |
|Extender un carácter a la derecha|**Mayús+Flecha derecha**| Edit.CharRightExtend |
|Final del documento|**Fin**| Edit.DocumentEnd |
|Extender al final del documento|**Mayús+Fin**| Edit.DocumentEndExtend |
|Inicio de documento|**Página principal**| Edit.DocumentStart |
|Extender al inicio del documento|**Mayús+Inicio**| Edit.DocumentStartExtend |
|Pestaña Insertar|**Tabulación**| Edit.InsertTab |
|Línea abajo|**Flecha abajo**| Edit.LineDown |
|Extender una línea abajo|**Mayús+Flecha arriba**| Edit.LineDownExtend |
|Línea arriba|**Flecha arriba**| Edit.LineUp |
|Extender una línea arriba|**Mayús+Flecha abajo**| Edit.LineUpExtend |
|Mover control hacia abajo|**Ctrl+Flecha abajo**| Edit.MoveControlDown |
|Mover el control a la izquierda|**Ctrl+Flecha izquierda**| Edit.MoveControlLeft |
|Mover el control a la derecha|**Ctrl+Flecha derecha**| Edit.MoveControlRight |
|Mover control hacia arriba|**Ctrl+Flecha arriba**| Edit.MoveControlUp |
|Cancelar selección|**Escape**| Edit.SelectionCancel |
|Ajustar tamaño de control por abajo|**Ctrl+Mayús+Flecha abajo**| Edit.SizeControlDown |
|Ajustar tamaño de control por la izquierda|**Ctrl+Mayús+Flecha izquierda**| Edit.SizeControlLeft |
|Ajustar tamaño de control por la derecha|**Ctrl+Mayús+Flecha derecha**| Edit.SizeControlRight |
|Ajustar tamaño de control por arriba|**Ctrl+Mayús+Flecha arriba**| Edit.SizeControlUp |
|Tabulación a la izquierda|**Mayús+Tab**| Edit.TabLeft |

### <a name="work-item-editor"></a>Editor de elementos de trabajo

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Crear copia del elemento de trabajo|**Mayús+Alt+C**| Edit.CreateCopyofWorkItem |
|Actualizar elemento de trabajo|**F5**| Edit.RefreshWorkItem |
|Nuevo elemento de trabajo vinculado|**Mayús+Alt+L**| Team.NewLinkedWorkItem |

### <a name="work-item-query-view"></a>Vista de consulta de elementos de trabajo

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Crear copia del elemento de trabajo|**Mayús+Alt+C**| Edit.CreateCopyofWorkItem |
|Aplicar sangría|**Mayús+Alt+Flecha derecha**| Edit.Indent |
|Anular sangría|**Mayús+Alt+Flecha izquierda**| Edit.Outdent |
|Nuevo elemento de trabajo vinculado|**Mayús+Alt+L**| Team.NewLinkedWorkItem |
|Actualizar|**F5**| Team.Refresh |
|Alternancia|**Mayús+Alt+V**| Window.Toggle |

### <a name="work-item-results-view"></a>Vista de resultados de elementos de trabajo

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Crear copia del elemento de trabajo|**Mayús+Alt+C**| Edit.CreateCopyofWorkItem |
|Aplicar sangría|**Mayús+Alt+Flecha derecha**| Edit.Indent |
|Anular sangría|**Mayús+Alt+Flecha izquierda**| Edit.Outdent |
|Ir al elemento de trabajo siguiente|**Mayús+Alt+N**| Team.GotoNextWorkItem |
|Ir al elemento de trabajo anterior|**Mayús+Alt+P**| Team.GotoPreviousWorkItem |
|Nuevo elemento de trabajo vinculado|**Mayús+Alt+L**| Team.NewLinkedWorkItem |
|Actualizar|**F5**| Team.Refresh |
|Alternancia|**Mayús+Alt+V**| Window.Toggle |

### <a name="workflow-designer"></a>Diseñador de flujo de trabajo

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Completar palabra|**Ctrl+K, W**<br /><br /> o<br /><br /> **Ctrl+K, Ctrl+W**<br /><br /> o<br /><br /> **Ctrl+Barra espaciadora**<br /><br /> o<br /><br /> **Alt+Flecha derecha**| Edit.CompleteWord |
|Reducir nivel de filtro|**Alt+,**| Edit.DecreaseFilterLevel |
|Aumentar nivel de filtro|**Alt+.**| Edit.IncreaseFilterLevel |
|Enumerar miembros|**Ctrl+K, L**<br /><br /> o<br /><br /> **Ctrl+K, Ctrl+L**<br /><br /> o<br /><br /> **Ctrl+J**| Edit.ListMembers |
|Información de parámetros|**Ctrl+K, P**<br /><br /> o<br /><br /> **Ctrl+K, Ctrl+P**<br /><br /> o<br /><br /> **Ctrl+Mayús+Barra espaciadora**| Edit.ParameterInfo |
|Información rápida|**Ctrl+K, I**<br /><br /> o<br /><br /> **Ctrl+K, Ctrl+I**| Edit.QuickInfo |
|Contraer|**Ctrl+E, Ctrl+C**<br /><br /> o<br /><br /> **Ctrl+E, C**| WorkflowDesigner.Collapse |
|Contraer todo|o| WorkflowDesigner.CollapseAll |
|Conectar nodos|**Ctrl+E, Ctrl+F**<br /><br /> o<br /><br /> **Ctrl+E, F**| WorkflowDesigner.ConnectNodes |
|Creación de variables|**Ctrl+E, Ctrl+N**<br /><br /> o<br /><br /> **Ctrl+E, N**| WorkflowDesigner.CreateVariable |
|Expandir todo|**Ctrl+E, Ctrl+X**<br /><br /> o<br /><br /> **Ctrl+E, X**| WorkflowDesigner.ExpandAll |
|Expandir en contexto|**Ctrl+E, Ctrl+E**<br /><br /> o<br /><br /> **Ctrl+E, E**| WorkflowDesigner.ExpandInPlace |
|Ir a principal|**Ctrl+E, Ctrl+P**<br /><br /> o<br /><br /> **Ctrl+E, P**| WorkflowDesigner.GoToParent |
|Mover enfoque|**Ctrl+E, Ctrl+M**<br /><br /> o<br /><br /> **Ctrl+E, M**| WorkflowDesigner.MoveFocus |
|Navegar por el diseñador|**Ctrl+Alt+F6**| WorkflowDesigner.NavigateThroughDesigner |
|Restauración|**Ctrl+E, Ctrl+R**<br /><br /> o<br /><br /> **Ctrl+E, R**| WorkflowDesigner.Restore |
|Mostrar u ocultar el diseñador de argumentos|**Ctrl+E, Ctrl+A**<br /><br /> o<br /><br /> **Ctrl+E, A**| WorkflowDesigner.ShowHideArgumentDesigner |
|Mostrar u ocultar el diseñador de importaciones|**Ctrl+E, Ctrl+I**<br /><br /> o<br /><br /> **Ctrl+E, I**| WorkflowDesigner.ShowHideImportsDesigner |
|Mostrar u ocultar el mapa de información general|**Ctrl+E, Ctrl+O** (letra "O")<br /><br /> o<br /><br /> **Ctrl+E, O**| WorkflowDesigner.ShowHideOverviewMap |
|Mostrar u ocultar el diseñador de variables|**Ctrl+E, Ctrl+V**<br /><br /> o<br /><br /> **Ctrl+E, V**| WorkflowDesigner.ShowHideVariableDesigner |
|Alternar selección|**Ctrl+E, Ctrl+S**<br /><br /> o<br /><br /> **Ctrl+E, S**| WorkflowDesigner.ToggleSelection |
|Acercamiento|**Ctrl+Núm +**| WorkflowDesigner.ZoomIn |
|Alejamiento|**Ctrl+Núm -**| WorkflowDesigner.ZoomOut |

### <a name="xaml-ui-designer"></a>Diseñador XAML

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Ajustar todo|**Ctrl+0** (cero)| Design.FitAll |
|Mostrar controladores|**F9**| Design.ShowHandles |
|Acercamiento|**Ctrl+Alt+=**| Design.ZoomIn |
|Alejamiento|**Ctrl+Alt+-**| Design.ZoomOut |
|Opciones del diseñador|**Ctrl+Mayús+;**|
|Edición de texto|**F2**| Format.EditText |
|All|**Ctrl+Mayús+R**| Format.ResetLayout.All |
|Ejecutar código del proyecto|**Ctrl+F9**|
|Ocultar (solo Blend)|**Ctrl+H**| Timeline.Hide (solo Blend) |
|Bloquear (solo Blend)|**Ctrl+L**| Timeline.Lock (solo Blend) |
|Mostrar (solo Blend)|**Ctrl+Mayús+H**| Timeline.Show (solo Blend) |
|Desbloquear (solo Blend)|**Ctrl+Mayús+L**| Timeline.Unlock (solo Blend) |
|Mover borde izquierdo a la izquierda|**Ctrl+Mayús+,**| View.EdgeLeftMoveLeft |
|Mover borde izquierdo a la derecha|**Ctrl+Mayús+,**| View.EdgeLeftMoveRight |
|Mover borde derecho a la izquierda|**Ctrl+Mayús+Alt+,**| View.EdgeRightMoveLeft |
|Mover borde derecho a la derecha|**Ctrl+Mayús+Alt+.**| View.EdgeRightMoveRight |
|Menú Mostrar marcador de propiedad|**Ctrl+Barra espaciadora**| View.ShowPropertyMarkerMenu |

### <a name="xml-text-editor"></a>Editor de XML (texto)

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|Iniciar depuración de XSLT|**Alt+F5**| XML.StartXSLTDebugging |
|Iniciar XSLT sin depurar|**Ctrl+Alt+F5**| XML.StartXSLTWithoutDebugging |

### <a name="xml-schema-designer"></a>Diseñador de esquemas XML

Los métodos abreviados de teclado específicos de este contexto son los siguientes:


|Comandos|Métodos abreviados de teclado|Identificador de comando|
|-|-|-|
|De abajo arriba|**Alt+Flecha arriba**| GraphView.BottomtoTop |
|De izquierda a derecha|**Alt+Flecha derecha**| GraphView.LefttoRight |
|De derecha a izquierda|**Alt+Flecha izquierda**| GraphView.RighttoLeft |
|De arriba abajo|**Alt+Flecha abajo**| GraphView.ToptoBottom |
|Quitar del área de trabajo|**Eliminar**| OtherContextMenus.GraphView.RemovefromWorkspace |
|Mostrar vista Modelo de contenido|**Ctrl+2**| XsdDesigner.ShowContentModelView |
|Mostrar vista Gráfico|**Ctrl+3**| XsdDesigner.ShowGraphView |
|Mostrar vista Inicio|**Ctrl+1**| XsdDesigner.ShowStartView |

## <a name="see-also"></a>Vea también

- [Comandos de Visual Studio](reference/visual-studio-commands.md)
