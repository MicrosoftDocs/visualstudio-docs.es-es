---
title: 'Cómo: Admitir la programación en un servicio de lenguaje heredado | Microsoft Docs'
description: Obtenga información sobre cómo proporcionar compatibilidad para la delineación, expansión o contención de diferentes regiones de texto en un servicio de lenguaje heredado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 028d1a9aae21aae8c6368e4eea3820aabd200be6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901804"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Cómo: Admitir la línea de texto en un servicio de lenguaje heredado
La línea de texto se usa para expandir o contraer distintas regiones de texto. La forma en que se usa la delineación se puede definir de forma diferente en distintos lenguajes. Para obtener más información, vea [Esquematización](../../ide/outlining.md).

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la manera más reciente de implementar características del servicio de lenguaje es usar extensiones MEF. Para obtener más información sobre la nueva manera de implementar la descripción, vea [Tutorial: Delinear](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Se recomienda empezar a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento del servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

 A continuación se muestra cómo admitir este comando para el servicio de lenguaje.

## <a name="to-support-outlining"></a>Para admitir la delineación

1. Implemente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> en el objeto de servicio de lenguaje.

2. Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> a en el objeto de sesión de esquematización actual para agregar nuevas regiones de esquema.

## <a name="robust-programming"></a>Programación sólida
 Cuando un usuario selecciona Contraer en  definiciones **en** el menú Esquematización, el IDE llama <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> a en el servicio de lenguaje.

 Cuando se llama a este método, el IDE pasa un puntero (un puntero a un búfer de texto) y un (un puntero a la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> sesión de delineación actual).

 Puede llamar al método <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> para varias regiones de esquema especificando estas regiones en el `rgOutlnReg` parámetro . El `rgOutlnReg` parámetro es una estructura <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> . Este proceso le permite especificar diferentes características de la región oculta, como si una región determinada está expandida o contraida.

> [!NOTE]
> Tenga cuidado al ocultar los caracteres de nueva línea. El texto oculto debe extenderse desde el inicio de la primera línea hasta el último carácter de la última línea de una sección, dejando visible el carácter final de nueva línea.

## <a name="see-also"></a>Consulta también
- [Cómo: Proporcionar compatibilidad con texto oculto en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Cómo: Proporcionar compatibilidad ampliada con la línea de subrayado en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
