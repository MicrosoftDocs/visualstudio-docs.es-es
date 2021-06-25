---
title: Constantes del IDE | Microsoft Docs
description: La clase VSConstants proporciona constantes específicas del IDE y que anteriormente solo se definieron en archivos de encabezado.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 802de0fd29d909320040667f972de422595bdd4f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904973"
---
# <a name="ide-constants"></a>Constantes ide

La clase proporciona constantes que son específicas del entorno de desarrollo integrado (IDE) y que se definieron <xref:Microsoft.VisualStudio.VSConstants> anteriormente solo en archivos de encabezado.

## <a name="logical-and-physical-views"></a>Vistas lógicas y físicas

|Valor|Descripción|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>Los controladores deben pasar este valor al método para obtener el cuadro de `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> diálogo **Abrir** con, en este caso, en las vistas de código posibles.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>Los controladores pasan este valor al método para obtener el cuadro de diálogo Abrir con , en este caso rellenado con posibles vistas de depuración que se asignan a la `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> misma vista que  <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid> .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>Los controladores pasan este valor al método para obtener el cuadro de `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> diálogo **Abrir** con, en este caso, para ver las vistas del diseñador **de** formularios.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>Los controladores pasan este valor al método para obtener el cuadro de diálogo Abrir con , en este caso la vista predeterminada `cmdidOpenWith` o principal del generador del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> editor. |
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>Los controladores pasan este valor al método para obtener el cuadro de diálogo Abrir con , en este para una vista del editor de texto de datos `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> o documentos. |
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>Los controladores pasan este valor al método , que solicita al usuario que elija la vista `cmdidOpenWith` definida por el usuario que se va a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> usar.|

## <a name="editor-factory-flags"></a>Marcas de generador del editor

|Valor|Descripción|
|-----------|-----------------|
|[Cef. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Marca obsoleta combinada bit a bit como primer parámetro del <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> método .|
|[Cef. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Combinado bit a bit como primer parámetro del método , esto indica que el <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> generador del editor debe realizar las correcciones necesarias.|
|[Cef. OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Combinado bit a bit como primer parámetro del <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> método, esta marca es mutuamente excluyente de [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[Cef. Silencioso](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Combinado bit a bit como primer parámetro del método , esto indica que el generador del editor debe crear el editor sin mostrar una interfaz <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> de usuario (UI).|

## <a name="visual-studio-errors"></a>Visual Studio errores

|Valor|Descripción|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Constante devuelta por las interfaces al comportamiento asincrónico cuando el objeto en cuestión ya está ocupado|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Error HRESULT que es específico de Visual Studio para "Datos de documento incompatibles".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Error HRESULT que es específico de Visual Studio y que indica "Paquete no cargado".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Error HRESULT que es específico de Visual Studio que indica que el "Proyecto ya existe".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Error HRESULT que es específico de Visual Studio y que indica que se produjo un error en la configuración del proyecto.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Error HRESULT que es específico de Visual Studio y que indica "Proyecto no cargado".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Error HRESULT que es específico de Visual Studio y que indica "Solución ya abierta".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Error HRESULT que es específico de Visual Studio y que indica "Solución no abierta".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Las interfaces de compilación que tienen parámetros para especificar una matriz de la interfaz, pero la implementación solo puede aplicar el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> a todas las salidas.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|El <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> método devuelve este valor si el documento tiene un formato que no se puede abrir en el editor.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Valor HRESULT que indica que el usuario ha hecho clic en el botón Atrás en un asistente Visual Studio datos.|

## <a name="visual-studio-constants"></a>Visual Studio constantes

|Valor|Descripción|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Error HRESULT que es específico de Visual Studio y que indica "Proyecto reenviado".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Constante que es específica de Visual Studio para un "marcador del cuadro de herramientas".|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Constante que es específica de Visual Studio para difundir un mensaje de notificación a través del método que <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> indica el principio de la modalidad.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Constante que es específica de Visual Studio para difundir un mensaje de notificación a través del método que indica <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> el final de la modalidad.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Constante que es específica de Visual Studio para difundir un mensaje de notificación a través del método que indica que las métricas de <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> la barra de comandos han cambiado.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Constante que es específica de Visual Studio que indica que no se ha establecido una cookie.|
|[VSITEMID. Nula](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Identificador Visual Studio elemento que representa la ausencia de un elemento de proyecto. Este valor se usa cuando no hay ninguna selección actual.|
|[VSITEMID. Raíz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Identificador Visual Studio elemento que representa la raíz de una jerarquía de proyecto y se usa para identificar toda la jerarquía, en lugar de un único elemento.|
|[VSITEMID. Selección](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Identificador Visual Studio elemento que representa el elemento o elementos seleccionados actualmente, que puede incluir la raíz de la jerarquía.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Describe qué componente del IDE se acaba de seleccionar, por <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> ejemplo, en una llamada.

|Constante|Valor|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VELEMID
 Constantes usadas para indicar un nuevo estado de selección.

|Constante|Valor|
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

|Constante|Valor|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>Consulta también

- [Comandos definidos por ide para extender sistemas de proyecto](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
