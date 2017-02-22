---
title: "Comandos importantes para los filtros de servicio de lenguaje | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Servicios de lenguaje, filtros"
  - "Servicios de lenguaje de comandos para admitir"
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Comandos importantes para los filtros de servicio de lenguaje
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Si desea crear un filtro totalmente representado del servicio de lenguaje, considere administrar los siguientes comandos.  La lista completa de identificadores de comandos se define en la enumeración de <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> para el código administrado y el archivo de encabezado de Stdidcmd.h para código no administrado de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .  Puede encontrar el archivo de Stdidcmd.h en *ruta de instalación de Visual Studio SDK*\\VisualStudioIntegration\\Common\\Inc.  
  
## comandos de administrar  
  
> [!NOTE]
>  no es obligatorio filtrar para cada comando en la tabla siguiente.  
  
|Command|Descripción|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado cuando el usuario hace clic con el botón secundario.  Este comando indica que es el momento de proporcionar un menú contextual.  Si no controla este comando, el editor de texto proporciona un menú contextual predeterminado sin comandos específicos del idioma.  Para incluir para sus propios comandos en este menú, controle el comando y mostrar un menú contextual personalmente.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado normalmente cuando el usuario CTRL\+J.  Llame al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para mostrar el cuadro de la finalización de instrucciones.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado cuando el usuario escribe un carácter.  Controle este comando para determinar cuando se escribe un carácter desencadenador y proporcionar la finalización de instrucciones, sugerencias de método, y marcadores de texto, como colorear la sintaxis, admiten coincidir, y marcadores de error.  Llame al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para la finalización de instrucciones y el método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> para las sugerencias de método.  Para admitir marcadores de texto, supervise este comando para determinar si el carácter que se escriben es necesario para actualizar los marcadores.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado al usuario la tecla ENTRAR.  Controle este comando para determinar cuándo cerrar una ventana de la sugerencia de método llamando al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>.  De forma predeterminada, la vista de texto controla este comando.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado al usuario la clave de reserva.  Monitor para determinar cuándo cerrar una ventana de la sugerencia de método llamando al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>.  De forma predeterminada, la vista de texto controla este comando.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado desde un menú o una tecla de método abreviado.  Llame al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para actualizar la ventana de sugerencias con la información de parámetros.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado cuando se desplaza el usuario sobre una variable o posiciones cursor respecto a una variable y se selecciona **información rápida** de **IntelliSense** en el menú de **Editar** .  Devuelve el tipo en una sugerencia llamando al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.  Si la depuración está activa, la sugerencia también debe mostrar el valor de la variable.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado normalmente cuando el usuario CTRL\+BARRA ESPACIADORA.  Este comando indica al servicio de lenguaje que llame al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Enviado desde un menú, normalmente de **Selección con comentarios** o de **Selección sin comentarios** de **AVANZADAS** en el menú de **Editar** .  <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica que desea marcar como comentario el texto seleccionado; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica que el usuario desea para no el texto seleccionado.  Estos comandos se pueden implementar solo por el servicio de lenguaje.|  
  
## Vea también  
 [Desarrollar un servicio de lenguaje](../../extensibility/internals/developing-a-legacy-language-service.md)