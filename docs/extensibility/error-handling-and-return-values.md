---
title: "Control de errores y valores devueltos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "control de errores [Visual Studio SDK]"
  - "control de errores"
  - "valores devueltos"
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Control de errores y valores devueltos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackages y COM utilizan la misma arquitectura de errores. El `SetErrorInfo` y `GetErrorInfo` funciones forman parte de la interfaz de programación de aplicaciones \(API\) de Win32. Cualquier VSPackage en el entorno de desarrollo integrado \(IDE\) puede llamar a estas API de Win32 global para registrar la información de error enriquecida al recibir una notificación de error. El [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] proporciona ensamblados de interoperabilidad para administrar la información de error.  
  
## Métodos de interoperabilidad  
 Para su comodidad, el IDE proporciona un método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, usar en lugar de llamar a las API de Win32. En el uso de código administrado <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>. Cuando un error `HRESULT` llega en el nivel donde debe mostrarse el mensaje de error \(suele ser el objeto de implementación de un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> controlador de comandos\), el IDE utiliza otro método, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, para mostrar el cuadro de mensaje adecuado. Código administrado utiliza la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> \(método\).  
  
 Como implementador de VSPackage, normalmente implementan objetos COM `ISupportErrorInfo`. El `ISupportErrorInfo` interfaz garantiza que la información de error enriquecida puede subir verticalmente la cadena de llamadas. Objetos que pueden utilizarse entre procesos o entre subprocesos deben admitir `ISupportErrorInfo` para asegurarse de que la información de error enriquecida correctamente se calculan referencias al llamador.  
  
 Todos los objetos relacionados con VSPackages y que estén implicados en ampliar el IDE, incluidos los generadores de editores, editores, jerarquías y ofrece servicios, deben admitir la información de error enriquecida. Mientras que el IDE no requieren estos objetos VSPackage implementar `ISupportErrorInfo`, siempre es recomendable hacerlo.  
  
 El IDE es responsable de la información de error y mostrar a un usuario de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] siempre que un `HRESULT` se propaga al IDE. El IDE también es el mecanismo para crear `ErrorInfo` objetos.  
  
## Instrucciones generales  
 Puede usar el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> métodos para establecer y notificar los errores internos de la implementación del paquete VSPackage. Sin embargo, como regla general, siga estas instrucciones para controlar los mensajes de error en el paquete VSPackage:  
  
-   Implemente `ISupportErrorInfo` en los objetos COM de VSPackage.  
  
-   Crear un error reporting mecanismo que llama el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método en objetos que implementan <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
-   Permitir que el IDE mostrar errores a los usuarios a través de la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> \(método\).  
  
## Información de error en el IDE  
 Las reglas siguientes indican cómo controlar la información de error en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:  
  
-   Como una estrategia defensiva para garantizar que no se notifica información de error obsoletos a los usuarios, las funciones que la llamada la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> método debe llamar primero el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método. Pasar `null` para borrar los mensajes de error almacenado en caché antes de llamar a algo que puede establecer la nueva información de error.  
  
-   Sólo se pueden llamar a funciones que no informan directamente mensajes de error del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método si va a devolver un error `HRESULT`. Es admisible para borrar el `ErrorInfo` en la entrada a una función o al devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK>. La única excepción a esta regla es cuando una llamada devuelve un error `HRESULT` del que puede recuperar explícitamente o pasar por alto la parte receptora.  
  
-   Cualquier persona que omite explícitamente un error `HRESULT` debe llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método con <xref:Microsoft.VisualStudio.VSConstants.S_OK>. De lo contrario, la `ErrorInfo` objeto podría utilizarse accidentalmente cuando otra parte, genera un error sin proporcionar sus propios `ErrorInfo`.  
  
-   Todos los métodos que se originen un error `HRESULT` se recomienda llamar a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método para proporcionar información de error enriquecida. Si el valor devuelto `HRESULT` es un especial `FACILITY_ITF` error y, a continuación, el método debe proporcionar adecuada `ErrorInfo`objeto. Si el error devuelto es un error del sistema estándar \(por ejemplo, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>, y así sucesivamente.\) es aceptable para devolver el código de error sin llamar explícitamente a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> \(método\). Como una estrategia de codificación defensiva, al que se origina un error `HRESULT` \(incluidos los errores del sistema\), llame siempre a la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método, ya sea con `ErrorInfo` que describe el error con mayor detalle o `null`.  
  
-   Llamar todas las funciones que devuelven un error originado por otra llamada debe pasar la información que se recibió el error en la `HRESULT` sin modificar el `ErrorInfo` objeto.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo \(Component Automation\)](http://msdn.microsoft.com/es-es/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](http://msdn.microsoft.com/es-es/03317526-8c4f-4173-bc10-110c8112676a)   
 [ISupportErrorInfo Interface](http://msdn.microsoft.com/es-es/42d33066-36b4-4a5b-aa5d-46682e560f32)