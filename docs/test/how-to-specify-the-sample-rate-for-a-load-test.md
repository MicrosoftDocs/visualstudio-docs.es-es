---
title: 'Cómo: Especificar la frecuencia de muestreo de los parámetros de ejecución de pruebas de carga en Visual Studio'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings
ms.assetid: 51cbe7d6-5dfd-4842-bca3-f7f8a665dc84
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 2184c027651bf604b6ab89e5b2e63b6e945b2355
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2018
ms.locfileid: "39382508"
---
# <a name="how-to-specify-the-sample-rate-for-a-load-test-run-setting"></a>Cómo: Especificar la frecuencia de muestreo de los parámetros de ejecución de pruebas de carga

Después de crear la prueba de carga con el **Asistente para prueba de carga nueva**, puede usar el **Editor de pruebas de carga** para cambiar las propiedades de modo que satisfagan las necesidades y los objetivos de la prueba.

Con el **Editor de pruebas de carga**, puede modificar valor de propiedad de configuración de ejecución **Frecuencia de muestreo** en la ventana **Propiedades**. Para obtener una lista completa de los parámetros de ejecución y sus descripciones, vea [Propiedades de los parámetros de ejecución de las pruebas de carga](../test/load-test-run-settings-properties.md).

Elija un valor apropiado para la propiedad **Frecuencia de muestreo** en los parámetros de ejecución de pruebas de carga según la duración de la prueba de carga. Una velocidad de muestra menor, como el valor predeterminado de cinco segundos, necesita más espacio en la base de datos de resultados de pruebas de carga. En el caso de pruebas de carga más largas, el incremento de la velocidad de muestra reduce la cantidad de datos recopilados. Para obtener más información, vea [Cómo: Especificar la frecuencia de muestreo de los parámetros de ejecución de pruebas de carga](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

He aquí algunas instrucciones sobre las velocidades de muestra:

|Duración de la prueba de carga|Tasa del ejemplo recomendada|
|------------------------|-----------------------------|
|\< 1 hora|5 segundos|
|De 1 a 8 horas|15 segundos|
|De 8 a 24 horas|30 segundos|
|> 24 horas|60 segundos|

## <a name="to-specify-performance-counter-sampling-rate-in-a-run-setting"></a>Para especificar la frecuencia de muestreo de los contadores de rendimiento en un parámetro de ejecución

1.  Abra una prueba de carga.

     Aparece el **Editor de pruebas de carga**. Se mostrará el árbol de la prueba de carga.

2.  En la carpeta **Parámetros de ejecución** del árbol de la prueba de carga, elija la configuración de ejecución para la que desea especificar la frecuencia de muestreo de la prueba.

3.  En el menú **Ver**, seleccione la ventana **Propiedades**.

     Las categorías y propiedades de los parámetros de ejecución se muestran en la ventana **Propiedades**.

4.  En la propiedad **Frecuencia de muestreo**, escriba un valor de tiempo de la frecuencia en la que la prueba de carga recopilará los datos del contador de rendimiento.

5.  Cuando haya terminado de cambiar la propiedad, elija **Guardar** en el menú **Archivo**. A continuación, puede ejecutar la prueba de carga con el nuevo valor de **Frecuencia de muestreo**.

## <a name="see-also"></a>Vea también

- [Configurar los parámetros de ejecución de pruebas de carga](../test/configure-load-test-run-settings.md)
- [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md)