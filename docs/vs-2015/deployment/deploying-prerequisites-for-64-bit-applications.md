---
title: Implementar requisitos previos de las aplicaciones de 64 bits | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 92f30e8e059475c907da184aa59a8e4b7a2cf19f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675565"
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>Implementar requisitos previos de aplicaciones de 64 bits
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La implementación de ClickOnce admite la instalación de aplicaciones en plataformas de 64 bits. Las plataformas de destino son **x86** para plataformas de 32 bits, **x64** para máquinas que admiten los conjuntos de instrucciones de AMD64 y EM64T, e **Itanium** para el procesador Itanium de 64 bits.  
  
## <a name="prerequisites"></a>Requisitos previos  
 En la tabla siguiente se enumeran los redistribuibles que puede usar como requisitos previos para la instalación de su aplicación de 64 bits.  
  
 Si selecciona un requisito previo que no tiene componentes de 64 bits, podría ver una advertencia que indica que los paquetes seleccionados no están disponibles para la plataforma de 64 bits.  
  
|Redistribuible|Compatibilidad con x64|Compatibilidad con IA64|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../includes/vsto-runtime-md.md)]|Sí|No|  
|Bibliotecas en tiempo de ejecución de Visual C++ 2010 (IA64)|No|Sí|  
|Bibliotecas en tiempo de ejecución de Visual C++ 2010 (x64)|Sí|No|  
|Microsoft .NET Framework 4 (x86 y x64)|Sí||  
|Microsoft .NET Framework 4 Client Profile (x86 y x64)|Sí||  
  
## <a name="see-also"></a>Vea también  
 [Implementar aplicaciones, servicios y componentes](../deployment/deploying-applications-services-and-components.md)   
 [Cómo: Instalar requisitos previos mediante una aplicación ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Aplicaciones de 64 bits](https://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)
