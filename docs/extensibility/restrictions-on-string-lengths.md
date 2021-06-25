---
title: Restricciones de longitudes de cadena | Microsoft Docs
description: Obtenga información sobre los límites en las longitudes de cadenas usadas por diversas funciones impuestas por la API del complemento de control de código fuente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7fd0d88a50f64aee1f0bc5c273d7a3cd50c6f53f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900257"
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
> La longitud no incluye la terminación `null` . Otras constantes con un sufijo "_SIZE" en lugar de "_LEN" incluyen espacio para la terminación `null` .

|Constante|Valor|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Consulta también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)
