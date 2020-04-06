---
title: 'Cómo: Esquema de soporte en un servicio de lenguaje heredado Microsoft Docs'
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707921"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>Cómo: Apoyar la esbozación en un servicio de lenguaje heredado
La esquematización se utiliza para expandir o contraer diferentes regiones de texto. La forma en que se utiliza la esquematización se puede definir de manera diferente por diferentes idiomas. Para obtener más información, vea [Esquematización](../../ide/outlining.md).

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información sobre la nueva forma de implementar la esquematización, consulte [Tutorial: esquematización](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

 A continuación se muestra cómo admitir este comando para el servicio de lenguaje.

## <a name="to-support-outlining"></a>Para apoyar la esbozación

1. Implementar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage> en el objeto de servicio de lenguaje.

2. Llame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> al objeto de sesión de esquematización actual para agregar nuevas regiones de esquema.

## <a name="robust-programming"></a>Programación sólida
 Cuando un usuario selecciona Contraer a **definiciones** en el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A> menú **Esquema,** el IDE llama al servicio de lenguaje.

 Cuando se llama a este método, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> el IDE pasa un puntero <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> (un puntero a un búfer de texto) y un (un puntero a la sesión de esquematización actual).

 Puede llamar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> al método para varias regiones de `rgOutlnReg` esquema especificando estas regiones en el parámetro. El `rgOutlnReg` parámetro <xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion> es una estructura. Este proceso le permite especificar diferentes características de la región oculta, como si una región determinada está expandida o contraída.

> [!NOTE]
> Tenga cuidado de ocultar caracteres de nueva línea. El texto oculto debe extenderse desde el inicio de la primera línea hasta el último carácter de la última línea de una sección, dejando el carácter final de la nueva línea visible.

## <a name="see-also"></a>Vea también
- [Cómo: Proporcionar soporte de texto oculto en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [Cómo: Proporcionar soporte de esquematización ampliada en un servicio de lenguaje heredado](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
