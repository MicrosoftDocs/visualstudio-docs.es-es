---
title: Analizar la cobertura de código en pruebas de comprobación de la compilación | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 59c07d15-511e-4fd0-b398-bde9d5ed00d9
caps.latest.revision: 10
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2442bf4cc31eeb51332aa28325924e18ccb1ffb7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660729"
---
# <a name="analyzing-code-coverage-in-build-verification-tests"></a>Analizar la cobertura de código en pruebas de comprobación de la compilación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El análisis de cobertura de código de Microsoft Visual Studio muestra que cantidad del código ejecutan las pruebas automatizadas. Para obtener más información, consulte [Usar cobertura de código para determinar la cantidad de código que se está probando](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

 Al insertar en el repositorio el código, las pruebas se ejecutarán en el servidor de compilación, junto con todas las demás pruebas de otros miembros del equipo. (Si todavía no lo ha configurado, consulte [ejecutar pruebas en el proceso de compilación](https://msdn.microsoft.com/library/d05743a1-c5cf-447e-bed9-bed3cb595e38)). Resulta útil analizar la cobertura de código en el servicio de compilación, porque proporciona la imagen más actualizada y completa de la cobertura en todo el proyecto. También se incluyen las pruebas del sistema automatizadas y otras pruebas codificadas que no se ejecutan normalmente en los equipos de desarrollo.

1. En Team Explorer, abra **Compilaciones** y agregue o modifique una definición de compilación.

2. En la página **Proceso**, expanda **Pruebas automatizadas**, **Origen de la prueba**, **Parámetros de ejecución**. Establezca **Tipo de archivo de parámetros de configuración** en **Cobertura de código habilitada**.

    Si tiene más de una definición de origen de la prueba, repita este paso para cada una.

   - <em>Pero no hay ningún campo denominado **Tipo de archivo de parámetros de ejecución</em>* .*

      En **Pruebas automatizadas**, seleccione **Ensamblado de prueba** y elija los puntos suspensivos **[...]** al final de la línea. En el cuadro de diálogo **Agregar o editar serie de pruebas**, en **Ejecutor de pruebas**, elija **Ejecutor de pruebas de Visual Studio**.

   ![Establecer la definición de compilación para cobertura de código](../test/media/codecoverage-plaincc.png "CodeCoverage-plainCC")

   Después de que la compilación se ejecute, los resultados de cobertura de código aparecen en el resumen de la compilación.

## <a name="see-also"></a>Vea también
 [Usar cobertura de código para determinar la cantidad de código que se está probando](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
