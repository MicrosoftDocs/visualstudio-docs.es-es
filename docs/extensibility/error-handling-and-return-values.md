---
title: Control de errores y valores devueltos | Microsoft Docs
description: Obtenga información sobre cómo el SDK de Visual Studio proporciona ensamblados de interoperabilidad para registrar información de error enriquecida cuando se recibe una notificación de error.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 530430852d621ea4aaf62bf2c86365609f26cf8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883381"
---
# <a name="error-handling-and-return-values"></a>Control de errores y valores devueltos
Los VSPackages y COM usan la misma arquitectura para los errores. Las `SetErrorInfo` `GetErrorInfo` funciones y forman parte de la interfaz de programación de aplicaciones (API) de Win32. Cualquier VSPackage en el entorno de desarrollo integrado (IDE) puede llamar a estas API de Win32 globales para registrar información de error enriquecida cuando se recibe una notificación de error. [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]Proporciona ensamblados de interoperabilidad para administrar la información de error.

## <a name="interop-methods"></a>Métodos de interoperabilidad
 Por comodidad, el IDE proporciona un método, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> , para usar en lugar de llamar a las API de Win32. En código administrado, use <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Cuando llega un error `HRESULT` en el nivel en el que se debe mostrar el mensaje de error (suele ser el objeto que implementa un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> controlador de comandos), el IDE usa otro método, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> , para mostrar el cuadro de mensaje adecuado. En código administrado, use el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> método.

 Como implementador de VSPackage, los objetos COM normalmente implementan `ISupportErrorInfo` . La `ISupportErrorInfo` interfaz garantiza que la información de error enriquecida puede moverse verticalmente hacia arriba en la cadena de llamadas. Los objetos que se pueden usar en los procesos o en todos los subprocesos deben admitir `ISupportErrorInfo` para asegurarse de que la información de error enriquecida se serializa de nuevo al autor de la llamada.

 Todos los objetos que están relacionados con VSPackages y que están implicados en la extensión del IDE, incluidos los generadores de editores, los editores, las jerarquías y los servicios ofrecidos, deben admitir información de error enriquecida. Aunque el IDE no requiere que se implementen estos objetos VSPackage `ISupportErrorInfo` , siempre se recomienda.

 El IDE es responsable de notificar la información de errores y mostrarla a un usuario de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cada vez que `HRESULT` se PROPAGA al IDE. El IDE es también el mecanismo para crear `ErrorInfo` objetos.

## <a name="general-guidelines"></a>Directrices generales
 Puede usar los <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> métodos y <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> para establecer e informar también de los errores que son internos de la implementación del VSPackage. Sin embargo, como regla general, siga estas instrucciones para controlar los mensajes de error en el VSPackage:

- Implemente `ISupportErrorInfo` en los objetos com de VSPackage.

- Cree un mecanismo de informes de errores que llame al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método en los objetos que implementan <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

- Permita que el IDE muestre errores a los usuarios a través del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> método.

## <a name="error-information-in-the-ide"></a>Información de error en el IDE
 Las siguientes reglas indican cómo controlar la información de error en el [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:

- Como estrategia defensiva para garantizar que la información de error obsoleta no se notifique a los usuarios, las funciones que llaman al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> método deben llamar primero al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método. Pase `null` para borrar los mensajes de error almacenados en caché antes de llamar a cualquier elemento que pueda establecer información de error nueva.

- Las funciones que no notifican directamente los mensajes de error solo pueden llamar al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método si devuelven un error `HRESULT` . Se permite borrar el `ErrorInfo` de la entrada a una función o cuando se devuelve <xref:Microsoft.VisualStudio.VSConstants.S_OK> . La única excepción a esta regla es cuando una llamada devuelve un error `HRESULT` del que la entidad de recepción puede recuperarse explícitamente o omitirse de forma segura.

- Cualquier entidad que ignore explícitamente un error `HRESULT` debe llamar al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método con <xref:Microsoft.VisualStudio.VSConstants.S_OK> . De lo contrario, el `ErrorInfo` objeto podría usarse accidentalmente cuando otra entidad genera un error sin proporcionar el suyo propio `ErrorInfo` .

- Se recomienda que todos los métodos que originen un error `HRESULT` llamen al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método para proporcionar información de error enriquecida. Si el devuelto `HRESULT` es un `FACILITY_ITF` error especial, se requiere que el método proporcione un `ErrorInfo` objeto adecuado. Si el error devuelto es un error del sistema estándar (por ejemplo,,, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> , <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> , etc.), es aceptable devolver el código de error sin llamar explícitamente al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método. Como estrategia de codificación defensiva, cuando se origina un error `HRESULT` (incluidos los errores del sistema), llame siempre al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método, ya sea con la `ErrorInfo` Descripción del error con mayor detalle, o `null` .

- Todas las funciones que devuelven un error originado por otra llamada deben pasar la información recibida de la llamada con error en el `HRESULT` sin modificar el `ErrorInfo` objeto.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (automatización de componentes)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [Interfaz ISupportErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
