---
title: Comandos importantes para filtros del servicio de lenguaje | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0e2e605a0725c2f88922d3e3ce899263171bc4d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726927"
---
# <a name="important-commands-for-language-service-filters"></a>Comandos importantes para los filtros del servicio de lenguaje
Si desea crear un filtro de servicio de lenguaje completo, considere la posibilidad de controlar los siguientes comandos. La lista completa de identificadores de comando se define en la enumeración <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> para el código administrado y el archivo de encabezado Stdidcmd. h para el código [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] no administrado. Puede encontrar el archivo Stdidcmd. h en la *ruta de instalación de Visual Studio SDK*\VisualStudioIntegration\Common\Inc.

## <a name="commands-to-handle"></a>Comandos que se van a controlar

> [!NOTE]
> No es obligatorio filtrar para todos los comandos de la tabla siguiente.

|Comando|Descripción|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario hace clic con el botón secundario. Este comando indica que es el momento de proporcionar un menú contextual. Si no controla este comando, el editor de texto proporciona un menú contextual predeterminado sin ningún comando específico del lenguaje. Para incluir sus propios comandos en este menú, controle el comando y muestre un menú contextual.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Normalmente se envía cuando el usuario escribe CTRL + J. Llame al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para mostrar el cuadro de finalización de instrucciones.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario escribe un carácter. Supervise este comando para determinar cuándo se escribe un carácter desencadenador y proporcionar la finalización de instrucciones, las sugerencias de método y los marcadores de texto, como el color de la sintaxis, la coincidencia de llaves y los marcadores de error. Llame al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para la finalización de instrucciones y el método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> en la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> para obtener sugerencias sobre el método. Para admitir marcadores de texto, supervise este comando para determinar si el carácter que se va a escribir requiere que actualice los marcadores.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario escribe la tecla entrar. Supervise este comando para determinar cuándo descartar una ventana de sugerencia de método llamando al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. De forma predeterminada, la vista de texto controla este comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario escribe la tecla de retroceso. Monitor para determinar cuándo descartar una ventana de sugerencia de método llamando al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. De forma predeterminada, la vista de texto controla este comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía desde un menú o una tecla de método abreviado. Llame al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para actualizar la ventana de sugerencia con la información de parámetros.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario mantiene el puntero sobre una variable o coloca el cursor en una variable y selecciona **información rápida** de **IntelliSense** en el menú **edición** . Devuelva el tipo de la variable en una sugerencia llamando al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Si la depuración está activa, la sugerencia también debe mostrar el valor de la variable.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Normalmente se envía cuando el usuario escribe CTRL + barra ESPACIAdora. Este comando indica al servicio de lenguaje que llame al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía desde un menú, normalmente con **comentarios de selección** o sin comentarios en la **selección** **avanzada** en el menú **edición** . <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica que el usuario desea comentar el texto seleccionado;  <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica que el usuario desea quitar el comentario del texto seleccionado. Estos comandos solo se pueden implementar mediante el servicio de lenguaje.|

## <a name="see-also"></a>Vea también
- [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)