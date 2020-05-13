---
title: Proveedor de símbolos (Symbol Provider) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712822"
---
# <a name="symbol-provider"></a>Proveedor de símbolos
Una implementación del evaluador de expresiones debe tener acceso a la información de depuración simbólica generada por el compilador de lenguaje para evaluar variables y expresiones. Lo hace consumiendo las interfaces de un proveedor de símbolos (SP), también denominado controlador de símbolos.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]proporciona SPs para código administrado, así como código nativo mediante el formato de archivo de símbolos de Base de datos de programa (PDB). A menos que haya una gran necesidad de que el programa utilice símbolos almacenados [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]en un formato personalizado, se recomienda que utilice los SP proporcionados por .

## <a name="implementation-notes"></a>Notas de implementación
 Los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motores de depuración esperan hablar con los SP mediante interfaces de Common Language Runtime (CLR). Como resultado, un SP que va a trabajar con los motores de depuración de Visual Studio debe admitir CLR. Puede encontrar una lista completa de todas las interfaces de depuración [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]de CLR en debugref.doc, que forma parte del archivo .

 Si el SP solo funcionará con el motor de depuración personalizado, puede implementar el SP como considere adecuado en función de las necesidades del motor de depuración.

## <a name="see-also"></a>Vea también
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
