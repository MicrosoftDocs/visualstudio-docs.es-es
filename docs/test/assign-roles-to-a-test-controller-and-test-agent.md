---
title: Roles de controlador de pruebas y agente de prueba
description: Aprenda a crear y configurar un escenario de prueba donde se usa un controlador de pruebas y un agente de prueba para distribuir las pruebas entre varias máquinas, todo ello mediante Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- testing, walkthroughs, test controller and test agents
- test agent, walkthrough
- walkthroughs [Visual Studio ALM] testing
- test controller, walkthrough
- walkthroughs, test controller and test agents
ms.assetid: 57ed43ae-4e67-4139-8aec-3e9fceb0a745
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 163cb3d541b054d22dc46df0b8e1e4735ac3fd50
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964672"
---
# <a name="assign-roles-to-a-test-controller-and-test-agent"></a>Asignar roles a un controlador de pruebas y a un agente de pruebas

En este artículo se explica cómo crear y configurar un entorno de prueba que usa un controlador de pruebas y un agente de prueba para distribuir las pruebas entre varias máquinas, todo ello mediante Visual Studio. También se describe cómo agregar adaptadores de datos y de diagnóstico a la configuración de pruebas.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Requisitos previos

- Crear pruebas unitarias o pruebas de IU codificada para ejecutarlas con la configuración de pruebas.

- Instalar un controlador de pruebas y agentes de prueba. Para más información sobre cómo instalar un controlador de pruebas y agentes de pruebas, vea [Instalar agentes y controladores de pruebas](../test/lab-management/install-configure-test-agents.md).

## <a name="to-create-and-configure-a-test-setting"></a>Para crear y configurar una configuración de pruebas

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **Elementos de la solución**, señale **Agregar** y, después, elija **Nuevo elemento**.

     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.

2. En el panel **Plantillas instaladas**, elija **Configuración de pruebas**.

3. En el cuadro **Nombre**, escriba **TestSettingDistributedTestWalkthrough**.

4. Haga clic en **Agregar**.

     El nuevo archivo *TestSettingDistributedTestWalkthrough.testsettings* de prueba aparece en el **Explorador de soluciones**, bajo la carpeta **Elementos de la solución**.

     Se muestra el cuadro de diálogo **Configuración de pruebas**. La página **General** está seleccionada.

     Ahora, puede modificar y guardar los valores de la configuración de pruebas.

5. En **Nombre**, escriba el nombre de la configuración de pruebas.

6. En **Descripción**, escriba **Configuración de prueba distribuida**.

7. Deje **Esquema de nombre predeterminado** seleccionado.

## <a name="to-assign-roles-to-a-test-controller-and-test-agents"></a>Para asignar roles a un controlador de pruebas y agentes de prueba

1. Elija **Roles**.

     Se mostrará la página **Roles**.

2. Para ejecutar la prueba de rendimiento remotamente, use la lista desplegable **Método de ejecución de las pruebas** y seleccione **Ejecución remota**.

3. En la lista desplegable **Controlador**, escriba el nombre de equipo del [controlador de pruebas](../test/lab-management/install-configure-test-agents.md).

    > [!NOTE]
    > Si es la primera vez que agrega un controlador, no se mostrará ningún controlador en la lista desplegable. Esta lista se rellena con controladores anteriores especificados en otras configuraciones de pruebas.

4. En **Roles**, elija **Agregar**.

5. En la fila resaltada bajo la columna **Nombre**, escriba **Prueba distribuida**.

## <a name="to-assign-a-diagnostic-and-data-adapter-to-your-test-setting"></a>Para asignar un adaptador de datos y de diagnóstico a la configuración de pruebas

1. Elija **Datos y diagnósticos**.

     Se mostrará la página **Datos y diagnósticos**.

2. En **Rol**, compruebe que el rol **Prueba distribuida** está seleccionado.

3. En **Datos y diagnóstico para el rol seleccionado**, seleccione los adaptadores **IntelliTrace** y **System Information**.

     Para más información sobre estos adaptadores y otros adaptadores que se pueden usar en una configuración de pruebas, vea [Configuración de pruebas unitarias](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

4. Elija **Hosts**.

5. (Opcional) Si la máquina se está ejecutando en una versión de 64 bits de Microsoft Windows y ha compilado la prueba con la configuración **Cualquier CPU**, use la lista desplegable **Ejecutar pruebas en procesos de 32 bits o 64 bits** y seleccione **Ejecutar pruebas en proceso de 64 bits en un equipo de 64 bits**.

    > [!TIP]
    > Para tener una flexibilidad máxima, compile los proyectos de prueba con la configuración **Cualquier CPU**. Después, se pueden ejecutar en ambos agentes de 32 y 64 bits. No supone ninguna ventaja compilar los proyectos de prueba con la configuración de **64 bits**.

6. Para guardar la nueva configuración de pruebas, elija **Aplicar**.

7. Elija **Cerrar**.

::: moniker range="vs-2017"

8. En el menú **Probar**, seleccione **Configuración de pruebas** > **Seleccionar archivo de configuración de pruebas** y, luego, elija el archivo *TestSettingDistributedTestWalkthrough.testsettings*.

::: moniker-end

::: moniker range=">=vs-2019"

8. En el menú **Prueba**, elija **Seleccionar archivo de configuración de pruebas**. Busque y seleccione el archivo *TestSettingDistributedTestWalkthrough.testsettings*.

::: moniker-end

9. Ejecute la prueba como de costumbre.

     Cuando el controlador de pruebas procesa pruebas unitarias y pruebas de interfaz de usuario codificadas, las divide en grupos de 100 y las envía a un equipo del agente de prueba. Por ejemplo, si tiene 250 pruebas unitarias y tres agentes de pruebas, las primeras 100 pruebas unitarias se enviarán a agente1, las 100 siguientes se enviarán a agente2 y las siguientes 50 se enviarán a agente3.

## <a name="see-also"></a>Vea también

- [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md)
