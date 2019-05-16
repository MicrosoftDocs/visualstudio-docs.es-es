---
title: Control de errores y valores devueltos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74e61e60384b3e98bf26eb8208696ecb9223efa3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696331"
---
# <a name="error-handling-and-return-values"></a>Control de errores y valores devueltos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackages y COM utilizan la misma arquitectura de errores. El `SetErrorInfo` y `GetErrorInfo` funciones forman parte de la interfaz de programación de aplicaciones (API) Win32. Cualquier VSPackage en el entorno de desarrollo integrado (IDE) puede llamar a estas API de Win32 global para registrar la información de error enriquecida cuando se recibe una notificación de error. El [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] proporciona ensamblados de interoperabilidad para administrar la información de error.  
  
## <a name="interop-methods"></a>Métodos de interoperabilidad  
 Para su comodidad, el IDE proporciona un método, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, para usar en lugar de llamar a las API de Win32. En el uso de código administrado <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>. Cuando un error `HRESULT` llega en el nivel donde debe mostrarse el mensaje de error (a menudo es el objeto de implementación de un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> controlador de comandos), el IDE usa otro método, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, para mostrar el cuadro de mensaje adecuado. Código administrado usando el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> método.  
  
 Como un implementador de VSPackage, los objetos COM normalmente implementan `ISupportErrorInfo`. El `ISupportErrorInfo` interfaz garantiza que la información de error enriquecida puede mover verticalmente de la cadena de llamada. Deben ser compatible con los objetos que se pueden usar en los procesos o entre subprocesos `ISupportErrorInfo` para asegurarse de que la información de error enriquecida se serializa correctamente al llamador.  
  
 Todos los objetos que están relacionadas con los paquetes VSPackage y que están implicados en ampliar el IDE, incluidos los generadores de editores, editores, jerarquías y ofrece servicios, deben admitir la información de error enriquecida. Mientras que el IDE no requieren estos objetos de VSPackage para implementar `ISupportErrorInfo`, siempre es recomendable hacerlo.  
  
 El IDE es responsable de notificar la información de error y de la visualización a un usuario de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] cada vez que un `HRESULT` se propaga al IDE. El IDE también es el mecanismo para crear `ErrorInfo` objetos.  
  
## <a name="general-guidelines"></a>Instrucciones generales  
 Puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> métodos para establecer y notificar los errores que son internos a su implementación del VSPackage. Sin embargo, como regla general, siga estas instrucciones para controlar los mensajes de error en el paquete de VS:  
  
- Implemente `ISupportErrorInfo` en sus objetos COM de VSPackage.  
  
- Crear un error que informa el mecanismo que llama a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método en objetos que implementan <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
- Permitir que el IDE de mostrar los errores a los usuarios a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> método.  
  
## <a name="error-information-in-the-ide"></a>Información de error en el IDE  
 Las reglas siguientes indican cómo controlar la información de error en la [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE:  
  
- Como una estrategia defensiva para garantizar que la información de error obsoletos no se notifica a los usuarios, las funciones que llaman a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> en primer lugar debe llamar al método el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método. Pasar `null` para borrar los mensajes de error almacenado en caché antes de llamar a cualquier cosa que puede establecer la nueva información de error.  
  
- Solo se pueden llamar a funciones que no informan de los mensajes de error directamente el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método si va a devolver un error `HRESULT`. Es admisible para borrar el `ErrorInfo` en la entrada a una función o al devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK>. La única excepción a esta regla es cuando una llamada devuelve un error `HRESULT` desde que el receptor puede recuperar explícitamente o pasar por alto.  
  
- Cualquier entidad que explícitamente hace caso omiso de un error `HRESULT` debe llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método con <xref:Microsoft.VisualStudio.VSConstants.S_OK>. En caso contrario, el `ErrorInfo` objeto podría utilizarse accidentalmente cuando otra entidad, genera un error sin proporcionar sus propios `ErrorInfo`.  
  
- Todos los métodos que se originan un error `HRESULT` se recomienda llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método para proporcionar información de error enriquecida. Si el valor devuelto `HRESULT` es un especial `FACILITY_ITF` error y, a continuación, el método es necesario para proporcionar una adecuada `ErrorInfo`objeto. Si el error devuelto es un error del sistema estándar (por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>y así sucesivamente.) es aceptable para devolver el código de error sin llamar explícitamente a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método. Como una estrategia defensiva codificación, al que se origina un error `HRESULT` (incluidos los errores del sistema), llame siempre a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método, ya sea con `ErrorInfo` que describe el error con más detalle o `null`.  
  
- Llamar todas las funciones que devuelven un error originado por otra llamada debe pasar la información que se recibió el error en la `HRESULT` sin modificar el `ErrorInfo` objeto.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (automatización de componentes)](https://msdn.microsoft.com/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](https://msdn.microsoft.com/03317526-8c4f-4173-bc10-110c8112676a)   
 [Interfaz ISupportErrorInfo](https://msdn.microsoft.com/42d33066-36b4-4a5b-aa5d-46682e560f32)
