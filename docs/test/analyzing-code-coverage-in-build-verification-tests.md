---
title: "Analizar la cobertura de código en pruebas de comprobación de la compilación | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59c07d15-511e-4fd0-b398-bde9d5ed00d9
caps.latest.revision: "8"
ms.author: douge
manager: douge
ms.openlocfilehash: 3dab1fb335bf1fa7a51faf8f298208c18ec87dc5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="analyzing-code-coverage-in-build-verification-tests"></a>Analizar la cobertura de código en pruebas de comprobación de la compilación
El análisis de cobertura de código de Microsoft Visual Studio muestra que cantidad del código ejecutan las pruebas automatizadas. Para obtener más información, consulte [Usar cobertura de código para determinar la cantidad de código que se está probando](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 Al insertar en el repositorio el código, las pruebas se ejecutarán en el servidor de compilación, junto con todas las demás pruebas de otros miembros del equipo. (Si aún no lo ha configurado, vea [Ejecutar pruebas en el proceso de compilación](http://msdn.microsoft.com/Library/d05743a1-c5cf-447e-bed9-bed3cb595e38)). Es útil analizar la cobertura de código del servicio de compilación, porque proporciona la imagen más actualizada y más completa de cobertura de todo el proyecto. También se incluyen las pruebas del sistema automatizadas y otras pruebas codificadas que no se ejecutan normalmente en los equipos de desarrollo.  
  
1.  En Team Explorer, abra **Compilaciones** y agregue o modifique una definición de compilación.  
  
2.  En la página **Proceso**, expanda **Pruebas automatizadas**, **Origen de la prueba**, **Parámetros de ejecución**. Establezca **Tipo de archivo de parámetros de configuración** en **Cobertura de código habilitada**.  
  
     Si tiene más de una definición de origen de la prueba, repita este paso para cada una.  
  
    -   *Pero no hay ningún campo denominado**Tipo de archivo de parámetros de ejecución**.*  
  
         En **Pruebas automatizadas**, seleccione **Ensamblado de prueba** y elija los puntos suspensivos **[...]** al final de la línea. En el cuadro de diálogo **Agregar o editar serie de pruebas**, en **Ejecutor de pruebas**, elija **Ejecutor de pruebas de Visual Studio**.  
  
 ![Establecer la definición de compilación para cobertura de código](../test/media/codecoverage-plaincc.png "CodeCoverage-plainCC")  
  
 Después de que la compilación se ejecute, los resultados de cobertura de código aparecen en el resumen de la compilación.  
  
## <a name="see-also"></a>Vea también  
 [Usar cobertura de código para determinar la cantidad de código que se está probando](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
