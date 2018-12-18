---
title: 'Cómo: admitir la esquematización en un servicio de lenguaje heredado | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b6f9ba947aee0276e2cca6270438cdaf20e7626e
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39510962"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Cómo: admitir la esquematización en un servicio de lenguaje heredado
Esquematización se utiliza para expandir o contraer las diferentes áreas de texto. Se usa el modo de esquematización pueden definirse de forma diferente a distintos idiomas. Para obtener más información, vea [Esquematización](../../ide/outlining.md).  
  
 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información acerca de la nueva forma de implementar la esquematización, vea [Tutorial: esquematización](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Se recomienda que comience a usar el nuevo editor de API tan pronto como sea posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
 La siguiente muestra cómo se admite este comando para el servicio de lenguaje.  
  
## <a name="to-support-outlining"></a>Para admitir la esquematización  
  
1.  Implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> en el objeto de servicio de lenguaje.  
  
2.  Llamar a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> en el objeto de sesión de esquematización actual para agregar nuevas regiones de esquema.  
  
## <a name="robust-programming"></a>Programación sólida  
 Cuando un usuario selecciona **contraer a definiciones** en el **esquematización** menú, las llamadas IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> en su servicio de lenguaje.  
  
 Cuando se llama a este método, el IDE se pasa en un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> puntero (un puntero a un búfer de texto) y un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (un puntero a la sesión actual de esquematización).  
  
 Puede llamar a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> método para varias regiones de esquema mediante la especificación de estas regiones en el `rgOutlnReg` parámetro. El `rgOutlnReg` parámetro es un <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> estructura. Este proceso le permite especificar distintas características de la región oculta, por ejemplo, si expande o contrae una región determinada.  
  
> [!NOTE]
>  Tenga cuidado sobre la ocultación de caracteres de nueva línea. Texto oculto debe ampliar desde el principio de la primera línea hasta el último carácter de la última línea en una sección, dejando el último carácter de nueva línea visible.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: proporcionar texto oculto admitir en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)   
 [Cómo: proporcionar compatibilidad con esquematización ampliada en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)