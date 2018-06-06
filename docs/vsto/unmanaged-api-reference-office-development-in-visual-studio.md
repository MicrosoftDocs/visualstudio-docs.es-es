---
title: Referencia de API no administrada (desarrollo de Office en Visual Studio)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, reference
- Office development in Visual Studio, unmanaged API reference
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 97388073d63b25bb17a7f49f4e2c5fb96bf2f572
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767902"
---
# <a name="unmanaged-api-reference-office-development-in-visual-studio"></a>Referencia de API no administrada (desarrollo de Office en Visual Studio)
  A partir de 2007 Microsoft Office system, aplicaciones de Office usan la [interfaz IManagedAddin](../vsto/imanagedaddin-interface.md) interfaz para llamar a un componente de cargador de inicio de complemento de VSTO que se incluye con la [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Este componente se usa para ayudar a cargar complementos de VSTO administrados. Puede crear su propio componente de cargador de complemento de VSTO implementando esta interfaz.  
  
> [!NOTE]  
>  ¿Está interesado en el desarrollo de soluciones que amplían la experiencia de Office en [varias plataformas](https://dev.office.com/add-in-availability)? Visite la nueva [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y complementos VSTO, y puede compilarlas mediante prácticamente cualquier tecnología, como HTML5, JavaScript, CSS3 y XML de programación web.  
  
## <a name="in-this-section"></a>En esta sección  
 [Interfaz IManagedAddin](../vsto/imanagedaddin-interface.md)  
 Una interfaz COM que se puede implementar para cargar y descargar complementos de VSTO administrados en las aplicaciones de Office.  
  
  