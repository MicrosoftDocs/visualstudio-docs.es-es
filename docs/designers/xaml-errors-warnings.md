---
title: Errores y advertencias de XAML
ms.date: 03/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: karann
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea8bf298f5847c779d2dc13154ddb27b2efeb214
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="xaml-errors-and-warnings"></a>Errores y advertencias de XAML

Al crear XAML, Visual Studio analiza el código a medida que lo escribe. Cuando se detecta un error, aparece un subrayado ondulado en una línea de código. Al mantener el mouse sobre el subrayado ondulado se proporciona más información sobre el error o la advertencia. Para algunos errores y advertencias, se muestra una bombilla Acción rápida y, a continuación, y mediante el método abreviado de teclado **Ctrl**+**.** se muestran las opciones para corregir el problema.

## <a name="error-types"></a>Tipos de error

En segundo plano, varias herramientas analizan el código XAML en paralelo. Los errores de XAML se categorizan en uno de los tres tipos siguientes, en función de la herramienta que detectó el error:

|**Error detectado por**|**Código del código de error**|
|--------------------------------|-----------------|
|Servicio de lenguaje XAML (editor XAML)|XLSxxxx|
|Diseñador XAML|XDGxxxx|
|Editar y continuar en XAML|XECxxxx|

> [!Note]
> No todos los errores o advertencias tienen un código correspondiente. Tales errores suelen ser errores del Diseñador XAML.


## <a name="suppress-xaml-designer-errors"></a>Supresión de los errores del Diseñador XAML

Abra el cuadro de diálogo **Opciones** seleccionando **Herramientas > Opciones** y luego seleccione **Editor de texto > XAML > Varios**.

Desactive la casilla **Show errors detected by the XAML designer** (Mostrar errores detectados por el Diseñador XAML).

![Supresión de errores del Diseñador XAML](../designers/media/suppress_xaml_designer_errors.PNG "SuppressXAMLDesignerErrors")


