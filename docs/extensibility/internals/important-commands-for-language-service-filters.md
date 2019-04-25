---
title: Filtros de comandos importantes para el lenguaje de servicio | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aff56ea4527fcc61c9b74c73df3b36c554c43072
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56602422"
---
# <a name="important-commands-for-language-service-filters"></a>Comandos importantes para los filtros del servicio de lenguaje
Si desea crear un filtro de servicio de lenguaje completo, considere la posibilidad de controlar los siguientes comandos. La lista completa de identificadores de comandos se define en el <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> enumeración para código administrado y el encabezado Stdidcmd.h de archivos para unmanaged [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] código. Puede encontrar el archivo Stdidcmd.h en *ruta de instalación del SDK de Visual Studio*\VisualStudioIntegration\Common\Inc.

## <a name="commands-to-handle"></a>Comandos para el identificador

> [!NOTE]
>  No es obligatorio para filtrar todos los comandos en la tabla siguiente.

|Comando|Descripción|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario hace clic con botón. Este comando indica que es el momento para proporcionar un menú contextual. Si no controla este comando, el editor de texto proporciona un menú de contextual predeterminado sin los comandos específicos del idioma. Para incluir sus propios comandos en este menú, controle el comando y mostrar un menú contextual por sí mismo.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Normalmente, se envía cuando el usuario escribe CTRL+J. Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para mostrar el cuadro de finalización de instrucción.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario escribe un carácter. Supervisión de este comando para determinar cuándo se escribe un carácter desencadenador y para proporcionar la instrucción de finalización, sugerencias de método y los marcadores de texto, como el color de sintaxis, coincidencia de llaves y marcadores de error. Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para finalización de instrucciones y la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> para sugerencias de método. Para admitir los marcadores de texto, supervise este comando para determinar si el carácter que se ha escrito requiere que actualice sus marcadores.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario escribe la tecla ENTRAR. Supervisar este comando para determinar cuándo se debe cerrar una ventana de sugerencia de método mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. De forma predeterminada, la vista de texto controla este comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario escribe la tecla RETROCESO. Monitor para determinar cuándo se debe cerrar una ventana de sugerencia de método mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. De forma predeterminada, la vista de texto controla este comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envía desde un menú o una tecla de método abreviado. Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para actualizar la ventana de sugerencia con la información de parámetros.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario mantenga el mouse sobre una variable o coloca el cursor en una variable y selecciona **información rápida** desde **IntelliSense** en el **editar** menú. Devolver el tipo de la variable en una sugerencia al llamar a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Si la depuración está activa, la sugerencia también debería mostrar el valor de la variable.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Normalmente, se envía cuando el usuario escribe CTRL+BARRA espaciadora. Este comando indica que el servicio de lenguaje para llamar a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado desde un menú, normalmente **selección con comentarios** o **selección sin comentarios** desde **avanzadas** en el **editar** menú. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica que el usuario desea para marcar como comentario el texto seleccionado; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica que el usuario desea quitar el comentario del texto seleccionado. Estos comandos solo se implementa el servicio de lenguaje.|

## <a name="see-also"></a>Vea también
- [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)