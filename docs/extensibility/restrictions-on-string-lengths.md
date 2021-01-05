---
title: Restricciones en las longitudes de cadena | Microsoft Docs
description: Obtenga información sobre los límites de las longitudes de las cadenas usadas por las distintas funciones impuestas por la API del complemento de control de código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5412e930937d029f803f5c6c2b4ddc9d396d9485
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715527"
---
# <a name="restrictions-on-string-lengths"></a>Restricciones en las longitudes de cadena
La API del complemento de control de código fuente limita las longitudes de las cadenas usadas en varias funciones.

## <a name="string-length-values"></a>Valores de longitud de cadena

|Constante|Valor|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> La longitud no incluye la terminación `null` . Otras constantes con un sufijo "_SIZE" en lugar de "_LEN" incluyen espacio para finalizar `null` .

|Constante|Valor|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Consulte también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
