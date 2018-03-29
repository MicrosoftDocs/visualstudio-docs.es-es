---
title: Especificar el número de iteraciones de prueba en un parámetro de ejecución de una prueba de carga en Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: c05326a7c21eb8c3836fbd2896cc9478d4b82e32
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Cómo: Especificar el número de iteraciones de prueba del parámetro de ejecución de una prueba de carga

Después de crear la prueba de carga con el **Asistente para prueba de carga nueva**, puede usar el **Editor de pruebas de carga** para cambiar las propiedades de los escenarios de modo que satisfagan las necesidades y los objetivos de la prueba. Para obtener más información, vea [Tutorial: Crear y ejecutar una prueba de carga](../test/walkthrough-create-and-run-a-load-test.md).

Con el **Editor de pruebas de carga**, puede modificar la propiedad **Iteraciones de prueba** de un valor de parámetro de ejecución en la ventana Propiedades. La propiedad **Iteraciones de prueba** especifica el número de iteraciones que se ejecutan en todas las pruebas unitarias y de rendimiento web en todos los escenarios de una prueba de carga con el **Editor de pruebas de carga**.

> [!NOTE]
>  Para obtener una lista completa de las propiedades y sus descripciones, vea [Propiedades de los parámetros de ejecución de las pruebas de carga](../test/load-test-run-settings-properties.md).

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>Para especificar el número de iteraciones de prueba en un parámetro de ejecución

1.  Abra una prueba de carga.

     El **Editor de pruebas de carga** se abre y muestra el árbol de la prueba de carga.

2.  En el árbol de la prueba de carga, en la carpeta **Parámetros de ejecución**, elija un parámetro de ejecución.

3.  En el menú **Ver**, seleccione la ventana **Propiedades** para ver las propiedades y categorías del parámetro de ejecución de carga.

4.  Establezca la propiedad **Usar iteraciones de prueba** en **True**.

5.  En la propiedad **Iteraciones de prueba**, escriba un número que indique la cifra de iteraciones de prueba que se van a ejecutar durante la prueba de carga.

6.  Cuando haya terminado de cambiar la propiedad, elija **Guardar** en el menú **Archivo**. Luego, puede ejecutar la prueba de carga con el nuevo valor de **Iteraciones de prueba**.

## <a name="see-also"></a>Vea también

- [Configurar los parámetros de ejecución de pruebas de carga](../test/configure-load-test-run-settings.md)
- [Propiedades de los escenarios de prueba de carga](../test/load-test-scenario-properties.md)