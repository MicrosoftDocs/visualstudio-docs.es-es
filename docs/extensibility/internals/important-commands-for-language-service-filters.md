---
title: Comandos importantes para filtros de servicio de lenguaje | Microsoft Docs
description: Obtenga información sobre los comandos importantes que debe admitir al crear un filtro de servicio de lenguaje completo en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8dd5f65248411a7ea6b892d5b4c800718456339f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899061"
---
# <a name="important-commands-for-language-service-filters"></a>Comandos importantes para los filtros del servicio de lenguaje
Si desea crear un filtro de servicio de lenguaje completo, considere la posibilidad de controlar los siguientes comandos. La lista completa de identificadores de comandos se define en la enumeración de código administrado y el archivo de encabezado <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Stdidcmd.h para código no [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] administrado. Puede encontrar el archivo Stdidcmd.h en Visual Studio de instalación del *SDK*\VisualStudioIntegration\Common\Inc.

## <a name="commands-to-handle"></a>Comandos que se controlarán

> [!NOTE]
> No es obligatorio filtrar por cada comando de la tabla siguiente.

|Comando|Descripción|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario hace clic con el botón derecho. Este comando indica que es el momento de proporcionar un menú contextual. Si no controla este comando, el editor de texto proporciona un menú contextual predeterminado sin ningún comando específico del idioma. Para incluir sus propios comandos en este menú, controle el comando y muestre usted mismo un menú contextual.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Normalmente se envía cuando el usuario presiona CTRL+J. Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método en para mostrar el cuadro de finalización de la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> instrucción.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario tipos un carácter. Supervise este comando para determinar cuándo se escribe un carácter desencadenador y proporcionar finalización de instrucciones, sugerencias de método y marcadores de texto, como colores de sintaxis, coincidencia de llaves y marcadores de error. Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método en para la finalización de la instrucción y al método en para <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> sugerencias de método. Para admitir marcadores de texto, supervise este comando para determinar si el carácter que se va a escribir requiere que actualice los marcadores.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario escribe la tecla Entrar. Supervise este comando para determinar cuándo descartar una ventana de sugerencias de método llamando al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> método en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . De forma predeterminada, la vista de texto controla este comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario pulsa la tecla Retroceso. Supervise para determinar cuándo descartar una ventana de sugerencias de método llamando al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> método en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . De forma predeterminada, la vista de texto controla este comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía desde un menú o una tecla de método abreviado. Llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> método en para actualizar la ventana de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sugerencias con la información de parámetros.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario mantiene el puntero sobre una variable o coloca el cursor en una variable y selecciona **Información** rápida de **IntelliSense** en el **menú** Editar. Devuelve el tipo de la variable en una sugerencia llamando al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> método en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . Si la depuración está activa, la sugerencia también debe mostrar el valor de la variable.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Normalmente se envía cuando el usuario presiona CTRL+BARRA ESPACIADORA. Este comando indica al servicio de lenguaje que llame al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía desde un menú, normalmente **selección de comentarios** o selección de **anulación** de comentario **desde Avanzado** en **el menú** Edición. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica que el usuario desea comentar el texto seleccionado; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica que el usuario desea deshacer la comentario del texto seleccionado. Estos comandos solo los puede implementar el servicio de lenguaje.|

## <a name="see-also"></a>Consulta también
- [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)
