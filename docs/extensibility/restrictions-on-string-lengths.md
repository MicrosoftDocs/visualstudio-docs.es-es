---
title: Restricciones en las longitudes de cadena | Microsoft Docs
description: Obtenga información sobre los límites de las longitudes de las cadenas usadas por las distintas funciones impuestas por la API del complemento de control de código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b7526494f5d64f7e02e63e5ec3012297af730e87
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068419"
---
# <a name="restrictions-on-string-lengths"></a>Restricciones en las longitudes de cadena
La API del complemento de control de código fuente limita las longitudes de las cadenas usadas en varias funciones.

## <a name="string-length-values"></a>Valores de longitud de cadena

|Constante|Value|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> La longitud no incluye la terminación `null` . Otras constantes con un sufijo "_SIZE" en lugar de "_LEN" incluyen espacio para finalizar `null` .

|Constante|Value|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Consulte también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
