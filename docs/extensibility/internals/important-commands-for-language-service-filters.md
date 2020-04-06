---
title: Comandos importantes para los filtros de servicio de lenguaje ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb29ee5b5a5359d6cfe34911656dfe9be015262e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707611"
---
# <a name="important-commands-for-language-service-filters"></a>Comandos importantes para los filtros del servicio de lenguaje
Si desea crear un filtro de servicio de lenguaje con todas las funciones, considere la posibilidad de controlar los siguientes comandos. La lista completa de identificadores <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> de comando se define en la enumeración para [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] el código administrado y el archivo de encabezado Stdidcmd.h para código no administrado. Puede encontrar el archivo Stdidcmd.h en la ruta de *instalación del SDK*de Visual Studio .

## <a name="commands-to-handle"></a>Comandos para manejar

> [!NOTE]
> No es obligatorio filtrar por cada comando de la tabla siguiente.

|Get-Help|Descripción|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario hace clic con el botón derecho. Este comando indica que es el momento de proporcionar un menú contextual. Si no controla este comando, el editor de texto proporciona un menú contextual predeterminado sin ningún comando específico del idioma. Para incluir sus propios comandos en este menú, controle el comando y muestre un menú contextual usted mismo.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Normalmente se envía cuando el usuario escribe CTRL+J. Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> en el para mostrar el cuadro de finalización de la instrucción.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario escribe un carácter. Supervise este comando para determinar cuándo se escribe un carácter de desencadenador y para proporcionar la finalización de instrucciones, sugerencias de método y marcadores de texto, como el color de sintaxis, la coincidencia de llaves y los marcadores de error. Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> en la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> finalización <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> de la instrucción for y el método en las sugerencias del método for. Para admitir marcadores de texto, supervise este comando para determinar si el carácter que se está escribiendo requiere que actualice los marcadores.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario escribe la tecla Intro. Supervise este comando para determinar cuándo se debe <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> descartar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>una ventana de sugerencia de método llamando al método en el archivo . De forma predeterminada, la vista de texto controla este comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario escribe la tecla Retroceso. Supervisar para determinar cuándo se debe descartar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>ventana de sugerencia de método llamando al método en el archivo . De forma predeterminada, la vista de texto controla este comando.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía desde un menú o una tecla de método abreviado. Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> en el para actualizar la ventana de sugerencia con la información del parámetro.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía cuando el usuario pasa el cursor sobre una variable o coloca el cursor en una variable y selecciona **Información rápida** de **IntelliSense** en el menú **Editar.** Devolver el tipo de la variable <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> en una <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>sugerencia llamando al método en el archivo . Si la depuración está activa, la sugerencia también debe mostrar el valor de la variable.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Normalmente se envía cuando el usuario escribe CTRL+BARRA ESPACIADORA. Este comando indica al servicio <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> de lenguaje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>que llame al método en el archivo .|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Se envía desde un menú, normalmente Selección de **comentarios** o Selección de **descomisade** de **Avanzado** en el menú **Edición.** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>indica que el usuario desea comentar el texto seleccionado; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> indica que el usuario desea quitar el comentario del texto seleccionado. Estos comandos solo se pueden implementar mediante el servicio de lenguaje.|

## <a name="see-also"></a>Vea también
- [Desarrollo de un servicio de lenguaje heredado](../../extensibility/internals/developing-a-legacy-language-service.md)
