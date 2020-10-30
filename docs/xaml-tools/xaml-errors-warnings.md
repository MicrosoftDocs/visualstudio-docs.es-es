---
title: Errores y advertencias de XAML
description: Obtenga información sobre errores y advertencias de XAML en Visual Studio, incluido cómo se clasifican los errores, cómo obtener información de errores y cómo buscar opciones para corregirlos.
ms.custom: SEO-VS-2020
ms.date: 03/06/2018
ms.topic: error-reference
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83a68273f4fbb2f66986c18c692b91b6e1829a4c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049219"
---
# <a name="xaml-errors-and-warnings"></a>Errores y advertencias de XAML

Al crear XAML, Visual Studio analiza el código a medida que lo escribe. Cuando se detecta un error, aparece un subrayado ondulado en una línea de código. Al mantener el mouse sobre el subrayado ondulado se proporciona más información sobre el error o la advertencia. En el caso de algunos errores y advertencias, se muestra una bombilla de acción rápida y el uso de **Ctrl** + **.** se muestran las opciones para corregir el problema.

## <a name="error-types"></a>Tipos de errores

En segundo plano, varias herramientas analizan el código XAML en paralelo. Los errores de XAML se categorizan en uno de los tres tipos siguientes, en función de la herramienta que detectó el error:

|**Error detectado por**|**Código del código de error**|**Versión de Visual Studio**|
| - |-----------------| - |
|Servicio de lenguaje XAML (editor XAML)|XLSxxxx| Todas las versiones |
|XAML Designer|XDGxxxx| Todas las versiones | 
|Editar XAML y continuar|XECxxxx| Visual Studio 2019 versión 16,1 o anterior |
|Recarga activa de XAML | XHRxxxx | Visual Studio 2019 versión 16,2 o posterior |

Para obtener más información sobre cómo cambiar la personalización de marca de la edición XAML & continúe como la recarga en caliente de XAML, consulte las notas de la [versión](https://docs.microsoft.com/visualstudio/releases/2019/release-notes-v16.2#wpfuwp-tooling)

> [!Note]
> No todos los errores o advertencias tienen un código correspondiente. Tales errores suelen ser errores del Diseñador XAML.

## <a name="suppress-xaml-designer-errors"></a>Supresión de los errores del Diseñador XAML

Abra el cuadro de diálogo **Opciones** seleccionando **Herramientas > Opciones** y luego seleccione **Editor de texto > XAML > Varios** .

Desactive la casilla **Show errors detected by the XAML designer** (Mostrar errores detectados por el Diseñador XAML).

![Supresión de los errores del Diseñador XAML](media/suppress_xaml_designer_errors.png)
