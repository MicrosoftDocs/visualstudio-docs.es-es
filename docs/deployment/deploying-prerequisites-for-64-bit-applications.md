---
title: Implementar requisitos previos de las aplicaciones de 64 bits | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c70b58577f8aa6e391215658afb7f8fa43c9bb5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928880"
---
# <a name="deploy-prerequisites-for-64-bit-applications"></a>Implementación de requisitos previos de aplicaciones de 64 bits
La implementación de ClickOnce admite la instalación de aplicaciones en plataformas de 64 bits. Las plataformas de destino son **x86** para plataformas de 32 bits, **x64** para máquinas que admiten los conjuntos de instrucciones de AMD64 y EM64T, e **Itanium** para el procesador Itanium de 64 bits.

## <a name="prerequisites"></a>Requisitos previos
 En la tabla siguiente se enumeran los redistribuibles que puede usar como requisitos previos para la instalación de su aplicación de 64 bits.

 Si selecciona un requisito previo que no tiene componentes de 64 bits, podría ver una advertencia que indica que los paquetes seleccionados no están disponibles para la plataforma de 64 bits.

| Redistribuible | Compatibilidad con x64 | Compatibilidad con IA64 |
| - |-------------|--------------|
| [!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)] | Sí | No |
| Bibliotecas en tiempo de ejecución de Visual C++ 2010 (IA64) | No | Sí |
| Bibliotecas en tiempo de ejecución de Visual C++ 2010 (x64) | Sí | No |
| Microsoft .NET Framework 4 (x86 y x64) | Sí | |
| Microsoft .NET Framework 4 Client Profile (x86 y x64) | Sí | |

## <a name="see-also"></a>Vea también
- [Implementar aplicaciones, servicios y componentes](../deployment/deploying-applications-services-and-components.md)
- [Cómo: Instalar requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Aplicaciones de 64 bits](/dotnet/framework/64-bit-apps)