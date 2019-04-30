---
title: Restricciones en las longitudes de cadena | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, restrictions on string lengths
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ade5e9ac188cd6c1b721ed276e0c4e2aff71f32
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434730"
---
# <a name="restrictions-on-string-lengths"></a>Restricciones en las longitudes de cadena
La API de complemento de Control de origen limita las longitudes de cadenas usadas en distintas funciones.

## <a name="string-length-values"></a>Valores de longitud de cadena

|Constante|Valor|
|--------------|-----------|
|`SCC_NAME_LEN`|31|
|`SCC_AUXLABEL_LEN`|31|
|`SCC_USER_LEN`|31|
|`SCC_PRJPATH_LEN`|300|

> [!NOTE]
> La longitud no incluye el carácter final `null`. Otras constantes con un sufijo "_Tamaño" en lugar de "_LEN" incluir espacio para la terminación `null`.

|Constante|Valor|
|--------------|-----------|
|SCC_NAME_SIZE|32|
|SCC_AUXLABEL_SIZE|32|
|SCC_USER_SIZE|32|
|SCC_PRJPATH_SIZE|301|

## <a name="see-also"></a>Vea también
- [Complementos de control de código fuente](../extensibility/source-control-plug-ins.md)