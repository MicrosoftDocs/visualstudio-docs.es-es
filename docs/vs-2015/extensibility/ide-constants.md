---
title: Constantes IDE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 18256996d829d34117caa11f4e581d8e54d738b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204037"
---
# <a name="ide-constants"></a>Constantes de IDE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La <xref:Microsoft.VisualStudio.VSConstants> clase proporciona las constantes que son específicas para el entorno de desarrollo integrado (IDE) y que se definieron anteriormente sólo en los archivos de encabezado.  
  
## <a name="logical-and-physical-views"></a>Vistas lógicas y físicas  
  
|Value|DESCRIPCIÓN|  
|-----------|-----------------|  
|[LOGVIEWID_Code_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.code_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` los controladores deben pasar este valor para el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para obtener el **abrir con** cuadro de diálogo, en este caso en las vistas de código posible.|  
|[LOGVIEWID_Debugging_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.debugging_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` los controladores de este valor para pasar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para obtener el **abrir con** cuadro de diálogo, en este caso se rellena con posibles <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> depuración de las vistas que se asignan a la misma vista que <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>.|  
|[LOGVIEWID_Designer_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.designer_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` controladores pasan este valor para el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para obtener el **abrir con** cuadro de diálogo, en este caso para **Ver formulario** las vistas del diseñador.|  
|[LOGVIEWID_Primary_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.primary_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` los controladores de este valor para pasar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para obtener el **abrir con** cuadro de diálogo, en este caso la vista predeterminada/primaria del generador del editor.|  
|[LOGVIEWID_TextView_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.textview_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` los controladores de este valor para pasar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para obtener el **abrir con** cuadro de diálogo, en este caso para una vista de editor de texto de datos o de documentos.|  
|[LOGVIEWID_UserChooseView_guid](/dotnet/api/microsoft.visualstudio.vsconstants.logviewid.userchooseview_guid?view=visualstudiosdk-2015)|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` los controladores de este valor para pasar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método que solicita al usuario elegir qué vista definida por el usuario para usar.|  
  
## <a name="editor-factory-flags"></a>Editor de marcas de fábrica  
  
|Valor|DESCRIPCIÓN|  
|-----------|-----------------|  
|[CEF.CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|Una marca obsoleta combinada bit a bit como primer parámetro de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> método.|  
|[CEF.CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|Combine bit a bit como primer parámetro de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, método, esto indica el generador de editores debe realizar las correcciones necesarias.|  
|[CEF.CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|Combine bit a bit como primer parámetro de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> método, esta marca es mutuamente exclusiva de [CEF. CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015).|  
|[CEF.CloneFile](/dotnet/api/microsoft.visualstudio.vsconstants.cef?view=visualstudiosdk-2015)|Combine bit a bit como primer parámetro de la <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> método, esto indica el generador de editores debe crear el editor sin mostrar una interfaz de usuario (UI).|  
  
## <a name="visual-studio-errors"></a>Errores de Visual Studio  
  
|Valor|DESCRIPCIÓN|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Una constante devuelta por las interfaces al comportamiento asincrónico cuando el objeto en cuestión ya no está disponible|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Un error HRESULT específico de Visual Studio para "datos incompatibles de documento".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Un error HRESULT que es específico de Visual Studio y que indica "Paquete no cargado".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Un error HRESULT que es específico de Visual Studio y que indica que el "Proyecto ya existe".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Un error HRESULT que es específico de Visual Studio y que indica "Error de configuración del proyecto".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Un error HRESULT que es específico de Visual Studio y que indica "Proyecto no cargado".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Un error HRESULT que es específico de Visual Studio y que indica "Solución ya abierta".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Un error HRESULT que es específico de Visual Studio y que indica "Solución no abrir".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Devuelto por las interfaces de compilación que tienen parámetros para especificar una matriz a partir del <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> interfaz, pero la implementación solo puede aplicar el método a todos los resultados.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|El <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> método devuelve este valor si el documento tiene un formato que no se puede abrir en el editor.|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Un valor HRESULT que indica que el usuario presionó el botón Atrás en un asistente de Visual Studio.|  
  
## <a name="visual-studio-constants"></a>Constantes de Visual Studio  
  
|Value|DESCRIPCIÓN|  
|-----------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Un error HRESULT que es específico de Visual Studio y que indica "Proyecto reenviado".|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Una constante específica de Visual Studio para un "marcador de cuadro de herramientas".|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Una constante que es específica de Visual Studio para difundir un mensaje de notificación a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> método que indica el principio de la modalidad.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Una constante que es específica de Visual Studio para difundir un mensaje de notificación a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> método que indica el final de la modalidad.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Una constante que es específica de Visual Studio para difundir un mensaje de notificación a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> método que indica que se han cambiado las métricas de la barra de comandos.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Una constante que es específica de Visual Studio que indica que no se ha establecido una cookie.|  
|[VSITEMID.Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Un identificador de elemento de Visual Studio que representa la ausencia de un elemento de proyecto. Este valor se utiliza cuando no hay ninguna selección actual.|
|[VSITEMID.Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Un identificador de elemento de Visual Studio que representa la raíz de una jerarquía de proyectos y se usa para identificar la jerarquía completa, en lugar de un solo elemento.|
|[VSITEMID.Selection](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Identificador de elemento de Visual Studio que representa el elemento seleccionado actualmente o elementos, que pueden incluir la raíz de la jerarquía.| 
  
## <a name="ivsselectionevents"></a>IVsSelectionEvents  
 Describe qué componente del IDE acaba de seleccionarse, en un <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> llamar, por ejemplo.  
  
|Constante|Valor|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0 x 2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0 x 3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1| 
  
## <a name="vsselelemid"></a>VSSELELEMID  
 Constantes usadas para indicar un nuevo estado de selección.  
  
|Constante|Value|  
|--------------|-----------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|  
  
## <a name="component-selector-dialog-constants"></a>Constantes de cuadro de diálogo Selector de componentes  
  
|Constante|Value|  
|--------------|-----------|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|  
  
## <a name="see-also"></a>Vea también  
 [Comandos definidos por el IDE para ampliar sistemas del proyecto](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
