---
title: Proveedor de símbolos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b90846d9494ee046cf9dc4a3e5de9ff033ea3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712822"
---
# <a name="symbol-provider"></a>Proveedor de símbolos
Una implementación del evaluador de expresiones debe tener acceso a la información de depuración simbólica generada por el compilador del lenguaje para evaluar variables y expresiones. Para ello, consume las interfaces de un proveedor de símbolos (SP), también denominado controlador de símbolos.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona SP para código administrado y código nativo mediante el formato de archivo de símbolos de la base de datos de programa (PDB). A menos que haya una gran necesidad de que el programa use símbolos almacenados en un formato personalizado, se recomienda usar las SPs suministradas por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="implementation-notes"></a>Notas de implementación
 Los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motores de depuración esperan comunicarse con los SPS mediante interfaces de Common Language Runtime (CLR). Como resultado, un SP que va a trabajar con los motores de depuración de Visual Studio debe admitir CLR. Puede encontrar una lista completa de todas las interfaces de depuración de CLR en debugref.doc, que forma parte de [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

 Si el SP va a trabajar solo con el motor de depuración personalizado, puede implementar el SP como considere adecuado en función de las necesidades del motor de depuración.

## <a name="see-also"></a>Vea también
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
