---
title: Proveedor de símbolos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d54494a8fa23e0714769863ac0fa2e5ddc1f4c2
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276980"
---
# <a name="symbol-provider"></a>Proveedor de símbolos
Una implementación del evaluador de expresiones debe tener acceso a la información de depuración simbólica generada por el compilador de lenguaje con el fin de evaluar variables y expresiones. Lo hace si consume las interfaces de un proveedor de símbolos (SP), también denominado un controlador de símbolos.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Proporciona SPs para código administrado, así como código nativo utilizando el formato de archivo de símbolos de base de datos de programa (PDB). A menos que haya una fuerte necesita para que el programa para utilizar los símbolos que se almacenan en un formato personalizado, se recomienda utilizar el Service Pack proporcionada por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="implementation-notes"></a>Notas sobre la implementación  
 El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motores de depuración que se esperan para comunicarse con el Service Pack mediante interfaces de Common Language Runtime (CLR). Como resultado, un Service Pack que trabajará con los motores de depuración de Visual Studio debe admitir el CLR. Encontrará una lista completa de todas las interfaces de depuración de CLR en debugref.doc, que forma parte de la [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)].  
  
 Si el SP funcionará sólo con el motor de depuración personalizado, puede implementar el SP como considere oportuno según las necesidades de su motor de depuración.  
  
## <a name="see-also"></a>Vea también  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)