---
title: Filtros de servicio de comandos importantes para el idioma | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c0fa4b408c43acbf2ec87bcfaca5135c9037af7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="important-commands-for-language-service-filters"></a>Comandos importantes para los filtros de servicio de lenguaje
Si desea crear un filtro de servicio de lenguaje completo, considere la posibilidad de controlar los siguientes comandos. La lista completa de identificadores de comandos se define en el <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> enumeración para código administrado y el encabezado de Stdidcmd.h de archivos para las no administradas [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] código. Puede encontrar el archivo Stdidcmd.h en *ruta de instalación del SDK de Visual Studio*\VisualStudioIntegration\Common\Inc.  
  
## <a name="commands-to-handle"></a>Comandos de identificador  
  
> [!NOTE]
>  No es obligatorio para filtrar todos los comandos en la tabla siguiente.  
  
|Comando|Descripción|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario seleccione. Este comando indica que es el momento para proporcionar un menú contextual. Si no controla este comando, el editor de texto proporciona un menú contextual de forma predeterminada sin los comandos específicos del idioma. Para incluir sus propios comandos de este menú, controlar el comando y mostrar un menú contextual usted mismo.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Normalmente se envía cuando el usuario escribe CTRL+J. Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para mostrar el cuadro de finalización de la instrucción.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario escribe un carácter. Supervisión de este comando para determinar cuándo se escribe un carácter desencadenador y para proporcionar la instrucción de finalización, sugerencias de método y los marcadores de texto, como el color de sintaxis, coincidencia de llaves y marcadores de error. Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para finalización de instrucciones y la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> para obtener sugerencias de método. Para admitir marcadores de texto, supervisar este comando para determinar si el carácter que se ha escrito requiere que actualice sus marcadores.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario escribe la tecla ENTRAR. Supervisar este comando para determinar cuándo se debe descartar una ventana de sugerencia de método mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. De forma predeterminada, la vista de texto controla este comando.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario escribe la tecla RETROCESO. Monitor para determinar cuándo se debe descartar una ventana de sugerencia de método mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. De forma predeterminada, la vista de texto controla este comando.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Envía desde un menú o una tecla de método abreviado. Llame a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para actualizar la ventana de sugerencia con la información de parámetros.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario mantiene el mouse sobre una variable o el cursor coloca en una variable y selecciona **Quick Info** de **IntelliSense** en el **editar** menú. Devolver el tipo de la variable en una sugerencia mediante una llamada a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Si se activa la depuración, la sugerencia también debe mostrar el valor de la variable.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Normalmente se envía cuando el usuario escribe CTRL + BARRA ESPACIADORA. Este comando indica al servicio de lenguaje para llamar a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> método en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado desde un menú, normalmente **selección con comentarios** o **selección sin comentarios** de **avanzadas** en el **editar** menú. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>indica que el usuario desea Comente el texto seleccionado; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica que el usuario desea quitar el comentario del texto seleccionado. Estos comandos pueden implementarse únicamente por el servicio de lenguaje.|  
  
## <a name="see-also"></a>Vea también  
 [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)