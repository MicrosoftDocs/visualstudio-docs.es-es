---
title: Errores y advertencias de XAML
ms.date: 03/06/2018
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8a36a91f40fd4857e50d5262c1598ee096697e7
ms.sourcegitcommit: 22deb247ad951e4971f27fdab413b158415d0584
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "82921332"
---
# <a name="xaml-errors-and-warnings"></a>Errores y advertencias de XAML

Al crear XAML, Visual Studio analiza el código a medida que lo escribe. Cuando se detecta un error, aparece un subrayado ondulado en una línea de código. Al mantener el mouse sobre el subrayado ondulado se proporciona más información sobre el error o la advertencia. En el caso de algunos errores y advertencias, se muestra una bombilla de acción rápida y el uso de **Ctrl**+**.** se muestran las opciones para corregir el problema.

## <a name="error-types"></a>Tipos de errores

En segundo plano, varias herramientas analizan el código XAML en paralelo. Los errores de XAML se categorizan en uno de los tres tipos siguientes, en función de la herramienta que detectó el error:

|**Error detectado por**|**Código del código de error**|
| - |-----------------|
|Servicio de lenguaje XAML (editor XAML)|XLSxxxx|
|XAML Designer|XDGxxxx|
|Editar y continuar en XAML|XECxxxx|

> [!Note]
> No todos los errores o advertencias tienen un código correspondiente. Tales errores suelen ser errores del Diseñador XAML.

## <a name="suppress-xaml-designer-errors"></a>Supresión de los errores del Diseñador XAML

Abra el cuadro de diálogo **Opciones** seleccionando **Herramientas > Opciones** y luego seleccione **Editor de texto > XAML > Varios**.

Desactive la casilla **Show errors detected by the XAML designer** (Mostrar errores detectados por el Diseñador XAML).

![Supresión de los errores del Diseñador XAML](media/suppress_xaml_designer_errors.png)
