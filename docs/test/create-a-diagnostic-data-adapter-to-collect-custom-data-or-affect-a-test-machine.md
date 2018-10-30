---
title: Creación de un adaptador de datos de diagnóstico para pruebas en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: e0a7815b57fa49239a0895e6733a13c5c83e99e1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860898"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Crear un adaptador de datos de diagnóstico para recopilar datos personalizados o afectar a un equipo de prueba

Es posible que desee crear su propio adaptador de datos de diagnóstico para recopilar información al ejecutar una prueba o quizás desee que el sistema se vea afectado como parte de la prueba. Por ejemplo, quizás desee recopilar los archivos de registro creados por la aplicación en pruebas y adjuntarlos a los resultados de pruebas, o bien ejecutar las pruebas cuando quede poco espacio en el disco del equipo. Con las API proporcionadas en Visual Studio Enterprise, puede escribir código para realizar tareas en puntos concretos de la serie de pruebas. Por ejemplo, puede realizar tareas al inicio de una ejecución de pruebas, antes y después de que se ejecute cada una de las pruebas y una vez que la ejecución de pruebas ha finalizado.

Puede usar un archivo de configuración para proporcionar los valores predeterminados al adaptador de datos de diagnóstico personalizado. Por ejemplo, puede proporcionar información acerca de la ubicación del archivo que desea recopilar y adjuntar a los resultados de pruebas, o cuánto espacio en disco desea que quede en el sistema. Esta información se puede establecer para cada configuración de pruebas que cree. Se puede mostrar y modificar con el editor predeterminado que se proporciona en Microsoft Test Manager o puede crear su propio control de usuario para usarlo como un editor. Cualquier cambio que se realice en la configuración del adaptador en el editor se guardará con la configuración de pruebas.

Si ejecuta las pruebas desde Visual Studio, debe establecer que esta configuración de pruebas esté activa. Para obtener más información sobre la configuración de pruebas, vea [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md).

## <a name="tasks"></a>Tareas

 Use los temas siguientes como ayuda para crear adaptadores de datos de diagnóstico:

|Tareas|Temas relacionados|
|-|-----------------------|
|**Crear un adaptador de datos de diagnóstico:** para crear un adaptador de datos de diagnóstico, se crea una biblioteca de clases y, a continuación, se usan las API del adaptador de datos de diagnóstico para recopilar la información que se desea o para impactar en un sistema de pruebas que se está usando para ejecutar las pruebas.|-   [Cómo: Crear un adaptador de datos de diagnóstico](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Instalar un adaptador de datos de diagnóstico personalizado:** para instalar el adaptador de datos de diagnóstico o un adaptador proporcionado por otros, cópielo en el directorio correcto.|-   [Cómo: Instalar un adaptador de datos de diagnóstico personalizado](../test/how-to-install-a-custom-diagnostic-data-adapter.md)|
|**Seleccionar un adaptador de datos de diagnóstico personalizado para usar durante la ejecución de las pruebas:** en su configuración de pruebas puede seleccionar qué adaptador de datos de diagnóstico desea usar durante la ejecución de las pruebas.|-   [Collect diagnostic data while testing (Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts) [Recopilar datos de diagnóstico durante las pruebas (Azure Test Plans)]<br />-   [Collect diagnostic data in manual tests (Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts) [Recopilar datos de diagnóstico en pruebas manuales (Azure Test Plans)]|
|**Configurar qué hace un adaptador de datos de diagnóstico:** puede configurar las opciones para controlar las acciones del adaptador de datos de diagnóstico en esa configuración de pruebas concreta.|-   [Cómo: Crear un editor personalizado para los datos del adaptador de datos de diagnóstico](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)|

## <a name="see-also"></a>Vea también

- [Proyecto de ejemplo para crear un adaptador de datos de diagnóstico](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)
- [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md)