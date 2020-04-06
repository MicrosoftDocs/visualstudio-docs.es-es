---
title: Manejo de errores y valores de devolución ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b6b9bff9056360f9ea840f47b1488f05bee872
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711933"
---
# <a name="error-handling-and-return-values"></a>Manejo de errores y valores devueltos
VSPackages y COM usan la misma arquitectura para los errores. Las `SetErrorInfo` `GetErrorInfo` funciones y forman parte de la interfaz de programación de aplicaciones (API) de Win32. Cualquier VSPackage en el entorno de desarrollo integrado (IDE) puede llamar a estas API globales de Win32 para registrar información de error enriquecida al recibir una notificación de error. Proporciona [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] ensamblados de interoperabilidad para administrar la información de error.

## <a name="interop-methods"></a>Métodos de interoperabilidad
 Como comodidad, el IDE proporciona <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>un método, , para usar en lugar de llamar a las API de Win32. En código <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>administrado use . Cuando un `HRESULT` error llega al nivel donde se debe mostrar el mensaje <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de error (a menudo es <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>el objeto que implementa un controlador de comandos), el IDE utiliza otro método, , para mostrar el cuadro de mensaje adecuado. En código administrado, utilice el <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> método.

 Como implementador de VSPackage, los `ISupportErrorInfo`objetos COM normalmente implementan . La `ISupportErrorInfo` interfaz garantiza que la información de error enriquecida puede moverse verticalmente hacia arriba de la cadena de llamadas. Los objetos que se pueden usar `ISupportErrorInfo` entre procesos o entre subprocesos deben admitir se deben admitir para asegurarse de que la información de error enriquecida se calcula correctamente al autor de la llamada.

 Todos los objetos que están relacionados con VSPackages y que están implicados en la extensión del IDE, incluidos los generadores de editores, editores, jerarquías y servicios ofrecidos, deben admitir información de error enriquecida. Aunque el IDE no requiere estos `ISupportErrorInfo`VSPackage objetos para implementar , siempre se recomienda.

 El IDE es responsable de informar de la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] información `HRESULT` de error y mostrarla a un usuario de cada vez que se propaga un al IDE. El IDE es también `ErrorInfo` el mecanismo para crear objetos.

## <a name="general-guidelines"></a>Directrices generales
 Puede usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> los <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> métodos y para establecer y notificar errores que son internos de la implementación de VSPackage también. Sin embargo, como regla general, siga estas directrices para controlar los mensajes de error en el VSPackage:

- Implementar `ISupportErrorInfo` en los objetos COM de VSPackage.

- Cree un mecanismo de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> informes de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>errores que llame al método en los objetos que implementan .

- Deje que el IDE muestre <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> errores a los usuarios a través del método.

## <a name="error-information-in-the-ide"></a>Información de error en el IDE
 Las reglas siguientes indican cómo controlar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la información de error en el IDE:

- Como una estrategia defensiva para garantizar que la información de error <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> obsoleto no <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> se notifica a los usuarios, las funciones que llaman al método primero deben llamar al método. Pase `null` para borrar los mensajes de error almacenados en caché antes de llamar a cualquier cosa que pueda establecer nueva información de error.

- Las funciones que no notifican directamente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> los mensajes de error `HRESULT`solo pueden llamar al método si devuelven un error. Es permisible borrar la `ErrorInfo` entrada a una función <xref:Microsoft.VisualStudio.VSConstants.S_OK>o al devolver . La única excepción a esta regla `HRESULT` es cuando una llamada devuelve un error desde el que la parte receptora puede recuperarse o omitirse de forma segura.

- Cualquier parte que omita `HRESULT` explícitamente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> un <xref:Microsoft.VisualStudio.VSConstants.S_OK>error debe llamar al método con . De lo `ErrorInfo` contrario, el objeto podría utilizarse accidentalmente `ErrorInfo`cuando otra parte genera un error sin proporcionar su propio archivo .

- Se recomienda a `HRESULT` todos los métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> que originan un error que llamen al método para proporcionar información de error enriquecida. Si el `HRESULT` devuelto `FACILITY_ITF` es un error especial, el `ErrorInfo`método es necesario para proporcionar un objeto adecuado. Si el error devuelto es un error <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>del <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>sistema estándar (por ejemplo, , , , , etc.) es aceptable devolver el código de error sin llamar explícitamente al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método. Como estrategia de codificación defensiva, `HRESULT` al originar un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> error (incluidos `ErrorInfo` los errores del sistema), `null`siempre llame al método, ya sea describiendo el error con mayor detalle, o .

- Todas las funciones que devuelven un error originado por otra llamada `HRESULT` deben `ErrorInfo` pasar la información que se recibió de la llamada con errores en el sin modificar el objeto.

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (automatización de componentes)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [Interfaz ISupportErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
