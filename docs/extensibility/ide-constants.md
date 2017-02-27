---
title: "Constantes IDE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDE, errores"
  - "vistas lógicas"
  - "errores [Visual Studio], IDE"
  - "Constantes de contexto de la interfaz de usuario"
  - "constantes, IDE de Visual Studio"
  - "IDE, constantes"
  - "vistas físicas"
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Constantes IDE
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La <xref:Microsoft.VisualStudio.VSConstants> clase proporciona constantes que son específicas para el entorno de desarrollo integrado \(IDE\) y que se definieron anteriormente sólo en los archivos de encabezado.  
  
## Vistas lógicas y físicas  
  
|Valor|Descripción|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` los controladores deben pasar este valor a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para obtener el **Abrir con** cuadro de diálogo, en este caso en las vistas de código posible.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` controladores de pasan este valor a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para obtener el **Abrir con** cuadro de diálogo, en este caso se rellena con posibles <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging> vistas que se asignan a la misma vista que la depuración <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Designer>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` controladores de pasan este valor a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para obtener el **Abrir con** cuadro de diálogo, en cuyo caso se **Vista formulario** vistas del diseñador.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Primary>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` controladores de pasan este valor a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para obtener el **Abrir con** cuadro de diálogo, en este caso, la vista predeterminada principal de la fábrica de editor.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_TextView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` controladores de pasan este valor a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para obtener el **Abrir con** cuadro de diálogo para una vista de editor de texto de datos o de documentos.|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_UserChooseView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` controladores de pasan este valor a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método que solicita al usuario que elija qué vista definida por el usuario que usará.|  
  
## Editor de marcas de fábrica  
  
|Valor|Descripción|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>|Un indicador obsoleto se combina bit a bit como primer parámetro de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> \(método\).|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENASNEW>|Combinar bit a bit como primer parámetro de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, método, indica el generador del editor debe realizar las correcciones necesarias.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENFILE>|Combinar bit a bit como primer parámetro de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> \(método\), esta marca es mutuamente exclusivo de <xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>.|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_SILENT>|Combinar bit a bit como primer parámetro de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> \(método\), esto indica el generador del editor debe crear el editor sin mostrar una interfaz de usuario \(UI\).|  
  
## Errores de Visual Studio  
  
|Valor|Descripción|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Una constante devuelta por interfaces al comportamiento asincrónico cuando el objeto en cuestión en ya está ocupado|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Un error HRESULT específico [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para "datos de documento Incompatible".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Un error HRESULT específico [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y que indica "No cargada el paquete".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Un error HRESULT específico [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y que indica que el "Proyecto ya existe".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Un error HRESULT específico [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y que indica "Error de configuración del proyecto".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Un error HRESULT específico [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y que indica "No cargado el proyecto."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Un error HRESULT específico [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y que indica "La solución ya está abierta."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Un error HRESULT específico [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y que indica "Solución no está abierta."|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Devuelto por las interfaces de generación que tienen parámetros para especificar una matriz de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> interfaz, pero la implementación sólo puede aplicar el método a todas las salidas.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|El <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> método devuelve este valor si el documento tiene un formato que no se puede abrir en el editor.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Un valor HRESULT que indica que el usuario pulsa el botón Atrás en una [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Asistente.|  
  
## Constantes de Visual Studio  
  
|Valor|Descripción|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Un error HRESULT específico [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y que indica "Proyecto reenviado".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Una constante que es específica de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para un "marcador de cuadro de herramientas".|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Una constante que es específica de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para difundir un mensaje de notificación a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> método que indica el principio de la modalidad.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Una constante que es específica de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para difundir un mensaje de notificación a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> método que indica el final de la modalidad.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Una constante que es específica de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para difundir un mensaje de notificación a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> método indicando que se han cambiado las métricas de la barra de comandos.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Una constante que es específica de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que indica que no se ha establecido una cookie.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>|Un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identificador del elemento que representa la ausencia de un elemento de proyecto. Este valor se utiliza cuando no hay ninguna selección actual.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>|Un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identificador del elemento que representa la raíz de una jerarquía de proyectos y se utiliza para identificar la jerarquía completa, en lugar de un solo elemento.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>|Un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] identificador del elemento que representa el elemento seleccionado actualmente o los elementos, que pueden incluir la raíz de la jerarquía.|  
  
## IVsSelectionEvents  
 Describe qué componente del IDE sólo ha seleccionado, en un <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> llama a, por ejemplo.  
  
|Constante|Valor|  
|---------------|-----------|  
|<xref:Microsoft.VisualStudio.VSConstants.DocumentFrame>|0 x 2|  
|<xref:Microsoft.VisualStudio.VSConstants.PropertyBrowserSID>|0 x 4|  
|<xref:Microsoft.VisualStudio.VSConstants.StartupProject>|0 x 3|  
|<xref:Microsoft.VisualStudio.VSConstants.UndoManager>|0 x 0|  
|<xref:Microsoft.VisualStudio.VSConstants.UserContext>|0 x 5|  
|<xref:Microsoft.VisualStudio.VSConstants.WindowFrame>|0 x 1|  
  
## VSSELELEMID  
 Constantes usadas para indicar un nuevo estado de selección.  
  
|Constante|Valor|  
|---------------|-----------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|  
  
## Constantes de cuadro de diálogo Selector de componentes  
  
|Constante|Valor|  
|---------------|-----------|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM\_USER \+ 1280|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM\_USER \+ 1281|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM\_USER \+ 1290|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM\_USER \+ 1287|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM\_USER \+ 1285|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM\_USER \+ 1288|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM\_USER \+ 1286|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM\_USER \+ 1289|  
  
## Vea también  
 [Comandos definidos por el IDE para ampliar sistemas del proyecto](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)