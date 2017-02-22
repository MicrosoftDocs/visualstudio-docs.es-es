---
title: "Intercepci&#243;n de comandos del servicio de lenguaje heredado | Microsoft Docs"
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
  - "comandos, interceptar el servicio de lenguaje"
  - "Servicios de lenguaje, la intercepción de comandos"
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Intercepci&#243;n de comandos del servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], puede tener los comandos de la intersección del servicio de lenguaje que la vista de texto deben de otra manera.  Esto es útil para el comportamiento específico del lenguaje que la vista de texto no administra.  Puede interceptar estos comandos agregando uno o más filtros de comando a la vista de texto del servicio de lenguaje.  
  
## Obtener y distribuyendo el comando  
 Un filtro de comando es un objeto de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> que controla algunas secuencias de caracteres o comandos clave.  Puede asociar más de un filtro de comando con una única vista de texto.  Cada vista de texto mantiene los filtros de una cadena de comandos.  Después de crear un nuevo filtro de comando, agregue el filtro a la cadena para la vista de texto adecuada.  
  
 Llame al método de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> en <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> para agregar el filtro de comando a la cadena.  Cuando se llama a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] devuelve otro filtro de comando al que puede pasar los comandos que el filtro de comando no controla.  
  
 Tiene las opciones siguientes para administrar de comando:  
  
-   Controle el comando y debe pasar el comando al filtro de comando siguiente en la cadena.  
  
-   Controle el comando y no pase el comando al filtro de comando siguiente.  
  
-   No controle el comando, pero pase el comando al filtro de comando siguiente.  
  
-   omita el comando.  No lo administrar en el filtro actual, y no lo pase al filtro siguiente.  
  
 Para obtener información sobre qué comandos debe administrar el servicio de lenguaje, vea [Comandos importantes para los filtros de servicio de lenguaje](../../extensibility/internals/important-commands-for-language-service-filters.md).