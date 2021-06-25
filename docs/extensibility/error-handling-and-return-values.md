---
title: Control de errores y valores devueltos | Microsoft Docs
description: Obtenga información sobre cómo Visual Studio SDK proporciona ensamblados de interoperabilidad para registrar información de error enriquez al recibir una notificación de error.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ef33936e3dc36d98cc88b1285aa0b198a84cbd59
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898326"
---
# <a name="error-handling-and-return-values"></a>Control de errores y valores devueltos
VsPackages y COM usan la misma arquitectura para los errores. Las `SetErrorInfo` funciones y forman parte de la interfaz de programación de aplicaciones `GetErrorInfo` (API) Win32. Cualquier VSPackage en el entorno de desarrollo integrado (IDE) puede llamar a estas API globales de Win32 para registrar información de error completa al recibir una notificación de error. proporciona [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] ensamblados de interoperabilidad para administrar información de errores.

## <a name="interop-methods"></a>Métodos de interoperabilidad
 Por comodidad, el IDE proporciona un método, , para usar en lugar de llamar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> las API de Win32. En código administrado, use <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Cuando llega un error al nivel donde se debe mostrar el mensaje de error (suele ser el objeto que implementa un controlador de comandos), el IDE usa otro método, , para mostrar el cuadro de mensaje `HRESULT` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> adecuado. En código administrado, use el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> método .

 Como implementador de VSPackage, los objetos COM normalmente implementan `ISupportErrorInfo` . La `ISupportErrorInfo` interfaz garantiza que la información de error enriquecida puede moverse verticalmente hacia arriba en la cadena de llamadas. Los objetos que se pueden usar entre procesos o subprocesos deben admitir para asegurarse de que la información de error enriquecida se serializa correctamente `ISupportErrorInfo` al autor de la llamada.

 Todos los objetos relacionados con VSPackages y que intervienen en la extensión del IDE, incluidos los generadores de editores, editores, jerarquías y servicios ofrecidos, deben admitir información de error enriquecida. Aunque el IDE no requiere que estos objetos VSPackage `ISupportErrorInfo` implementen , siempre se recomienda.

 El IDE es responsable de notificar información de error y mostrarla a un usuario de cada vez que se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] `HRESULT` propaga al IDE. El IDE también es el mecanismo para crear `ErrorInfo` objetos.

## <a name="general-guidelines"></a>Directrices generales
 También puede usar los <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> métodos y para establecer y notificar los errores internos de la implementación de VSPackage. Sin embargo, como regla general, siga estas directrices para controlar los mensajes de error en el VSPackage:

- Implemente `ISupportErrorInfo` en los objetos COM de VSPackage.

- Cree un mecanismo de informes de errores que llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método en objetos que implementan <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

- Permita que el IDE muestre errores a los usuarios a través del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> método .

## <a name="error-information-in-the-ide"></a>Información de error en el IDE
 Las reglas siguientes indican cómo controlar la información de error en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:

- Como estrategia defensiva para garantizar que la información de error obsoleta no se notifica a los usuarios, las funciones que llaman al método deben llamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> primero al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método . Pase para borrar `null` los mensajes de error almacenados en caché antes de llamar a cualquier cosa que pueda establecer información de error nueva.

- Las funciones que no informan directamente de mensajes de error solo pueden llamar al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método si devuelven un error `HRESULT` . Está permitido borrar en la entrada `ErrorInfo` de una función o al devolver <xref:Microsoft.VisualStudio.VSConstants.S_OK> . La única excepción a esta regla es cuando una llamada devuelve un error del que la parte receptora puede recuperar explícitamente `HRESULT` o omitir de forma segura.

- Cualquier entidad que omite explícitamente un error `HRESULT` debe llamar al método con <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.VSConstants.S_OK> . De lo contrario, `ErrorInfo` el objeto podría usarse accidentalmente cuando otra parte genera un error sin proporcionar su propio `ErrorInfo` .

- Se recomienda que todos los métodos que originan un error `HRESULT` llamen al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método para proporcionar información de error completa. Si el devuelto `HRESULT` es un `FACILITY_ITF` error especial, el método es necesario para proporcionar un objeto `ErrorInfo` adecuado. Si el error devuelto es un error estándar del sistema (por ejemplo, , , , y así <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> sucesivamente), es aceptable devolver el código de error sin llamar explícitamente al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método . Como estrategia de codificación defensiva, al originar un error (incluidos los errores del sistema), llame siempre al método , ya sea describiendo el error con más detalle `HRESULT` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> o `ErrorInfo` `null` .

- Todas las funciones que devuelven un error originado por otra llamada deben pasar la información que se recibió de la llamada con error en sin `HRESULT` modificar el `ErrorInfo` objeto .

## <a name="see-also"></a>Consulta también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (Automatización de componentes)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [ISupportErrorInfo (interfaz)](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
