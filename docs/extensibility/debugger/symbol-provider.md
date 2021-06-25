---
title: Proveedor de símbolos | Microsoft Docs
description: Obtenga información sobre los proveedores de símbolos que Visual Studio para permitir que un evaluador de expresiones evalúe variables y expresiones.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3332bbf705d8e3149d864dbb35418fd4c12c523b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902922"
---
# <a name="symbol-provider"></a>Proveedor de símbolos
Una implementación del evaluador de expresiones debe tener acceso a la información de depuración simbólica generada por el compilador del lenguaje para evaluar variables y expresiones. Para ello, consume las interfaces de un proveedor de símbolos (SP), también denominado controlador de símbolos.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] proporciona SPs para código administrado, así como código nativo mediante el formato de archivo de símbolos Program DataBase (PDB). A menos que haya una gran necesidad de que el programa use símbolos almacenados en un formato personalizado, se recomienda usar los SP proporcionados por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="implementation-notes"></a>Notas de implementación
 Los [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motores de depuración esperan hablar con los SPs mediante interfaces de Common Language Runtime (CLR). Como resultado, un SP que va a trabajar con el Visual Studio de depuración debe admitir CLR. Puede encontrar una lista completa de todas las interfaces de depuración CLR en debugref.doc, que forma parte de [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] .

 Si el SP solo va a funcionar con el motor de depuración personalizado, puede implementar el SP como le parezca adecuado en función de las necesidades del motor de depuración.

## <a name="see-also"></a>Consulta también
- [Componentes del depurador](../../extensibility/debugger/debugger-components.md)
