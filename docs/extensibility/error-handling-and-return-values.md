---
title: Control de errores y los valores devueltos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cfbeef2de041cfd71fbf163d7860d903a6cb59e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135524"
---
# <a name="error-handling-and-return-values"></a>Control de errores y valores devueltos
VSPackages y COM utilizan la misma arquitectura de errores. El `SetErrorInfo` y `GetErrorInfo` funciones forman parte de la interfaz de programación de aplicaciones (API) de Win32. Cualquier paquete de VS en el entorno de desarrollo integrado (IDE) puede llamar a estos global las API de Win32 para registrar la información de error enriquecida cuando se recibe una notificación de error. El [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] proporciona ensamblados de interoperabilidad para administrar la información de error.  
  
## <a name="interop-methods"></a>Métodos de interoperabilidad  
 Para su comodidad, el IDE proporciona un método, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, que se usarán en lugar de llamar a las API de Win32. En el uso de código administrado <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>. Cuando un error `HRESULT` llega en el nivel donde debe mostrarse el mensaje de error (suele ser el objeto de implementación de un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> controlador de comandos), el IDE usa otro método, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, para mostrar el cuadro de mensajes adecuado. Código administrado usando el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> método.  
  
 Como un implementador de VSPackage, los objetos COM se implementan normalmente `ISupportErrorInfo`. El `ISupportErrorInfo` interfaz garantiza que la información de error enriquecida puede subir verticalmente la cadena de llamadas. Deben ser compatible con objetos que podrían usarse entre procesos o entre subprocesos `ISupportErrorInfo` para asegurarse de que la información de error enriquecida correctamente se serializa de vuelta al llamador.  
  
 Todos los objetos que están relacionadas con VSPackages y que están implicados en ampliar el IDE, incluidos los generadores de editores, editores, jerarquías y ofrecen servicios, deben admitir la información de error enriquecida. Mientras que el IDE no requieren estos objetos de VSPackage para implementar `ISupportErrorInfo`, siempre es recomendable hacerlo.  
  
 El IDE es responsable de la notificación de la información de error y mostrar a un usuario de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] siempre que sea un `HRESULT` se propaga al IDE. El IDE también es el mecanismo para crear `ErrorInfo` objetos.  
  
## <a name="general-guidelines"></a>Instrucciones generales  
 Puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> métodos para establecer y notificar los errores internos de la implementación de VSPackage también. Sin embargo, como regla general, siga estas directrices para controlar mensajes de error en el paquete de VS:  
  
-   Implemente `ISupportErrorInfo` en los objetos COM de VSPackage.  
  
-   Crear un error reporting mecanismo que llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método en objetos que implementan <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
-   Permitir que el IDE muestra los errores a los usuarios a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> método.  
  
## <a name="error-information-in-the-ide"></a>Información de error en el IDE  
 Las reglas siguientes indican cómo controlar la información de error en la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:  
  
-   Que una estrategia de defensa para garantizar que la información del error obsoleto no se notifica a los usuarios, las funciones que llaman los <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> método se debería llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método. Pasar `null` para borrar los mensajes de error almacenado en caché antes de llamar a algo que puede establecer la nueva información de error.  
  
-   Solo se permiten llamar a funciones que no informan directamente mensajes de error del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método si va a devolver un error `HRESULT`. Está permitido para borrar la `ErrorInfo` en la entrada a una función o al devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK>. La única excepción a esta regla es cuando una llamada devuelve un error `HRESULT` del que la entidad de recepción puede recuperar explícitamente o pasar por alto.  
  
-   Cualquier persona que omite explícitamente un error `HRESULT` debe llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método con <xref:Microsoft.VisualStudio.VSConstants.S_OK>. En caso contrario, el `ErrorInfo` objeto podría utilizarse accidentalmente cuando otro usuario genera un error sin proporcionar sus propios `ErrorInfo`.  
  
-   Todos los métodos que se originen un error `HRESULT` se recomienda llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método para proporcionar información de error enriquecida. Si el valor devuelto `HRESULT` es una clase especial `FACILITY_ITF` errores y, a continuación, el método es necesario para proporcionar un propios `ErrorInfo`objeto. Si el error devuelto es un error del sistema estándar (por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>y así sucesivamente.) es aceptable para devolver el código de error sin llamar explícitamente a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método. Como una estrategia de codificación defensiva, al que se origina un error `HRESULT` (incluidos los errores del sistema), llame siempre a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método, ya sea con `ErrorInfo` que describe el error con más detalle, o `null`.  
  
-   Llamar todas las funciones que devuelven un error originado por otra llamada debe pasar la información que se recibió desde el error en la `HRESULT` sin modificar el `ErrorInfo` objeto.  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (automatización de componentes)](http://msdn.microsoft.com/en-us/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/en-us/03317526-8c4f-4173-bc10-110c8112676a)   
 [Interfaz ISupportErrorInfo](http://msdn.microsoft.com/en-us/42d33066-36b4-4a5b-aa5d-46682e560f32)