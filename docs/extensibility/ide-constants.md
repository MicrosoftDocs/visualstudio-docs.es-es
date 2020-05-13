---
title: Constantes iDE ? Microsoft Docs
ms.date: 03/22/2018
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2eddac1cc7d7e616deb197752adf41a4d68d15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710501"
---
# <a name="ide-constants"></a>Constantes IDE

La <xref:Microsoft.VisualStudio.VSConstants> clase proporciona constantes que son específicas del entorno de desarrollo integrado (IDE) y que se definieron anteriormente solo en archivos de encabezado.

## <a name="logical-and-physical-views"></a>Vistas lógicas y físicas

|Value|Descripción|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` los controladores deben pasar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> este valor al método para obtener el cuadro de diálogo **Abrir con,** en este caso en posibles vistas de código.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` los controladores pasan <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> este valor al método para obtener el cuadro <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> de diálogo **Abrir** con, en este caso rellenado con posibles vistas de depuración que se asignan a la misma vista que <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` los controladores pasan <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> este valor al método para obtener el cuadro de diálogo **Abrir con,** en este caso para ver vistas del diseñador **de** formularios.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` los controladores pasan <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> este valor al método para obtener el cuadro de diálogo **Abrir con,** en este caso la vista predeterminada/primaria de la fábrica del editor.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` los controladores pasan <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> este valor al método para obtener el cuadro de diálogo **Abrir con,** en este para una vista del editor de texto de datos o documentos.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` los controladores pasan <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> este valor al método que solicita al usuario que elija qué vista definida por el usuario que se va a usar.|

## <a name="editor-factory-flags"></a>Banderas de fábrica de editor

|Value|Descripción|
|-----------|-----------------|
|[Cef. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Un indicador obsoleto combinado bit a <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> bit como el primer parámetro del método.|
|[Cef. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Combinado bit a bit como <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>el primer parámetro del método , esto indica que el generador del editor debe realizar las correcciones necesarias.|
|[Cef. OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Combinado bit a bit como <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> el primer parámetro del método, este indicador es mutuamente excluyente de [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[Cef. Silencioso](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Combinado bit a bit como <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> el primer parámetro del método, esto indica que el generador del editor debe crear el editor sin mostrar una interfaz de usuario (UI).|

## <a name="visual-studio-errors"></a>Errores de Visual Studio

|Value|Descripción|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Una constante devuelta por las interfaces al comportamiento asincrónico cuando el objeto en cuestión ya está ocupado|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Un error HRESULT que es específico de Visual Studio para "Datos de documento incompatibles".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Un error HRESULT que es específico de Visual Studio y que indica "Paquete no cargado."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Un error HRESULT que es específico de Visual Studio y que indica que el "Proyecto ya existe."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Un error HRESULT que es específico de Visual Studio y que indica "Error de configuración del proyecto."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Un error HRESULT que es específico de Visual Studio y que indica "Proyecto no cargado."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Un error HRESULT que es específico de Visual Studio y que indica "Solución ya abierta."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Un error HRESULT que es específico de Visual Studio y que indica "Solución no abierta."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Devuelta por las interfaces de compilación que <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> tienen parámetros para especificar una matriz de la interfaz, pero la implementación solo puede aplicar el método a todas las salidas.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|El <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> método devuelve este valor si el documento tiene un formato que no se puede abrir en el editor.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Un valor HRESULT que indica que el usuario pulsa el botón Atrás en un asistente de Visual Studio.|

## <a name="visual-studio-constants"></a>Constantes de Visual Studio

|Value|Descripción|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Un error HRESULT que es específico de Visual Studio y que indica "Proyecto reenviado."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Constante específica de Visual Studio para un "marcador de cuadro de herramientas".|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Constante específica de Visual Studio para transmitir un <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> mensaje de notificación a través del método que indica el principio de la modalidad.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Constante específica de Visual Studio para transmitir un <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> mensaje de notificación a través del método que indica el final de la modalidad.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Constante específica de Visual Studio para transmitir un <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> mensaje de notificación a través del método que indica que las métricas de la barra de comandos han cambiado.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Constante específica de Visual Studio que indica que no se ha establecido una cookie.|
|[VSITEMID. Nula](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Identificador de elemento de Visual Studio que representa la ausencia de un elemento de proyecto. Este valor se utiliza cuando no hay ninguna selección actual.|
|[VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Identificador de elemento de Visual Studio que representa la raíz de una jerarquía de proyecto y se usa para identificar toda la jerarquía, a diferencia de un único elemento.|
|[VSITEMID. Selección](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Identificador de elemento de Visual Studio que representa el elemento o elementos seleccionados actualmente, que puede incluir la raíz de la jerarquía.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Describe qué componente del IDE se acaba <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> de seleccionar, por ejemplo, en una llamada.

|Constante|Value|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Constantes utilizadas para indicar un nuevo estado de selección.

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

## <a name="component-selector-dialog-constants"></a>Constantes de diálogo del selector de componentes

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

- [Comandos definidos por IDE para ampliar los sistemas de proyectos](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
