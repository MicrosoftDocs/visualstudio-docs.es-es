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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bd1720553592b0cfbac8be412002ef1b39bfd5bf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836961"
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

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
