---
title: 'Cómo: admitir la esquematización en un servicio de lenguaje heredado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28396d513c83ed83e2769e75a6020a98b10251b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707921"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Cómo: admitir la esquematización en un servicio de lenguaje heredado
La esquematización se usa para expandir o contraer diferentes regiones de texto. La forma en que se usa la esquematización se puede definir de forma diferente en distintos lenguajes. Para obtener más información, vea [Esquematización](../../ide/outlining.md).

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar las características del servicio de lenguaje es usar extensiones de MEF. Para obtener más información sobre la nueva manera de implementar la esquematización, vea [Tutorial: esquematización](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Le recomendamos que empiece a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

 A continuación se muestra cómo admitir este comando para su servicio de lenguaje.

## <a name="to-support-outlining"></a>Para admitir la esquematización

1. Implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> en su objeto de servicio de lenguaje.

2. Llame a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> en el objeto de sesión de esquematización actual para agregar nuevas regiones de esquema.

## <a name="robust-programming"></a>Programación sólida
 Cuando un usuario selecciona **contraer a definiciones** en el menú **esquematización** , el IDE llama a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> en su servicio de lenguaje.

 Cuando se llama a este método, el IDE pasa un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> puntero (un puntero a un búfer de texto) y un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (un puntero a la sesión de esquematización actual).

 Puede llamar al <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> método para varias regiones de esquema especificando estas regiones en el `rgOutlnReg` parámetro. El `rgOutlnReg` parámetro es una <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> estructura. Este proceso permite especificar distintas características de la región oculta, por ejemplo, si se expande o se contrae una región determinada.

> [!NOTE]
> Tenga cuidado al ocultar los caracteres de nueva línea. El texto oculto debe extenderse desde el principio de la primera línea hasta el último carácter de la última línea de una sección, quedando visible el carácter de nueva línea final.

## <a name="see-also"></a>Vea también
- [Cómo: proporcionar compatibilidad de texto oculto en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Cómo: proporcionar compatibilidad de esquematización ampliada en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
