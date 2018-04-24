---
title: 'Cómo: Seleccionar un repositorio de resultados de pruebas de carga en Visual Studio | Microsoft Docs'
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.dialog.connectstringmissing
- vs.test.load.dialog.databaseconnectstring
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
- SQL, Load Test Results Store
ms.assetid: fa0c4dd9-612f-4a57-b8eb-458f129d9cda
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 3b653ff4bd57c9986e2269c20a4fb314a9372b23
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-select-a-load-test-results-repository"></a>Cómo: Seleccionar un repositorio de resultados de pruebas de carga

el usuario no está limitado a un almacén de resultados local. Con frecuencia, las pruebas de carga se ejecutan en un conjunto remoto de equipos agente. Los agentes, junto con un controlador, pueden generar más carga simulada que cualquier equipo único. Para obtener más información, vea [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md).

Los resultados de prueba de los agentes o un equipo local se pueden guardar en cualquier servidor SQL en el que se haya creado un almacén de resultados de pruebas de carga. En cualquier caso, debe identificar dónde desea almacenar los resultados de pruebas de carga mediante la ventana Administrar controladores de prueba.

Para obtener más información sobre los agentes, vea [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md).

## <a name="identify-a-results-store-for-load-test-data"></a>Identificar un almacén de resultados para datos de una prueba de carga

1.  En el **Explorador de soluciones**, abra el archivo de prueba de carga.

2.  En la barra de herramientas **Prueba de carga**, elija **Administrar controladores de pruebas**. Se mostrará el cuadro de diálogo Administrar Test Controller. Si está utilizando un agente de forma remota, debe seleccionar un controlador.

     ![Propiedades de la conexión del almacén de resultados de pruebas de carga](../test/media/loadtestconnectionproperties.png "LoadTestConnectionProperties") Propiedades de la conexión del almacén de resultados de pruebas de carga

3.  En el **Almacén de resultados de pruebas de carga**, haga clic en (…) para ver el cuadro de diálogo **Propiedades de la conexión**.

4.  En **Nombre del servidor**, escriba el nombre del servidor donde ha ejecutado los scripts `LoadTest`.

    > [!TIP]
    > Si está usando SQL Express en el equipo local para el almacén de pruebas de carga, escriba \<nombreDeEquipo>\sqlexpress (por ejemplo, **MyComputer\sqlexpress**).

5.  En **Conexión con el servidor**, puede elegir **Utilizar autenticación de Windows**. Puede especificar el nombre de usuario y la contraseña, pero, si lo hace, debe seleccionar la opción **Guardar mi contraseña**.

6.  En **Establecer conexión con una base de datos**, elija **Seleccione o escriba el nombre de la base de datos**. Seleccione **LoadTest** en el cuadro de lista desplegable.

7.  Elija **Aceptar**. Puede probar la conexión si elige **Probar conexión**.

8.  Elija **Cerrar** en el cuadro de diálogo **Administrar controlador de pruebas**.

## <a name="see-also"></a>Vea también

- [Administrar los resultados de pruebas de carga en el repositorio de resultados pruebas de carga](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md)