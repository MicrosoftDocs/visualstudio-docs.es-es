---
title: Crear una configuración de pruebas para una prueba de carga distribuida
description: Aprenda a realizar la configuración de pruebas de sus pruebas de carga para que pueda distribuirlas entre varias máquinas por medio de agentes de prueba y controladores de pruebas.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- test settings, for distributed load tests
ms.assetid: b63d4b71-3b74-4872-b2d1-f0bd1a9a8544
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 4ca0058d1f06e00941766ed1ecf6f81d73939a8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877998"
---
# <a name="how-to-create-a-test-settings-file-for-a-distributed-load-test"></a>Procedimiento: Creación de un archivo de configuración de pruebas para una prueba de carga distribuida

Establezca la *configuración de pruebas* de sus pruebas de carga para que pueda distribuir dichas pruebas entre varias máquinas por medio de agentes de prueba y controladores de pruebas. También puede establecer la configuración de pruebas para usar *adaptadores de datos de diagnóstico*, que especifican los tipos de datos que se van a recopilar o cómo afectan a los equipos de pruebas cuando se ejecutan las pruebas de carga desde Visual Studio.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Por ejemplo, puede usar el adaptador de datos de diagnóstico de Generador de perfiles de ASP.NET para recopilar el desglose de rendimiento del código. Además, los adaptadores de datos de diagnóstico se pueden usar para simular posibles cuellos de botella en la máquina de prueba o para reducir la memoria disponible del sistema.

La configuración de pruebas para Visual Studio se almacena en un archivo. La configuración de pruebas define la siguiente información sobre cada rol:

- Conjunto de roles que se requieren para la aplicación objeto de la prueba

- Rol que se va a usar para realizar las pruebas

- Adaptadores de datos de diagnóstico que se van a usar para cada rol

Cuando se ejecutan pruebas, se selecciona la configuración de pruebas que se va a usar como configuración activa según los requisitos para la ejecución de pruebas en cuestión. El archivo de la configuración de pruebas se almacena como parte de la solución. El nombre de archivo tiene la extensión *.testsettings*.

Cuando se agrega un proyecto de prueba de carga y rendimiento web a una solución, se crea un archivo *Default.testsettings*. El archivo se agrega automáticamente a la solución en la carpeta **Elementos de la solución**. Este archivo ejecuta las pruebas localmente sin adaptadores de datos de diagnóstico. Puede agregar otro archivo *.testsettings* o editar un archivo *.testsettings* existente a fin de especificar los adaptadores de datos de diagnóstico y los controladores de pruebas.

El controlador de pruebas tendrá agentes que se pueden utilizar para cada rol en la configuración de pruebas. Para obtener más información sobre los controladores de pruebas y los agentes de pruebas, vea [Administrar controladores de pruebas y agentes de pruebas con Visual Studio](../test/manage-test-controllers-and-test-agents.md).

Siga estos procedimientos con el fin de crear y quitar de una solución una configuración de pruebas para las pruebas de carga que desea ejecutar desde Visual Studio.

## <a name="create-a-test-settings-file"></a>Creación de un archivo de configuración de pruebas

1. En el **Explorador de soluciones**, haga clic con el botón derecho en **Elementos de la solución**, elija **Agregar** y luego **Nuevo elemento**.

     Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.

2. En el panel **Plantillas instaladas**, elija **Configuración de pruebas**.

3. (Opcional) En el cuadro **Nombre**, cambie el nombre del archivo de la configuración de pruebas.

4. Haga clic en **Agregar**.

     El nuevo archivo de la configuración de pruebas aparece en el **Explorador de soluciones**, en la carpeta **Elementos de la solución**.

5. Se muestra el cuadro de diálogo **Configuración de pruebas**. La página **General** está seleccionada.

     Ahora, puede modificar y guardar los valores de la configuración de pruebas.

6. En **Nombre**, escriba el nombre de la configuración de pruebas.

7. (Opcional) Bajo **Descripción**, escriba una descripción de la configuración de pruebas de modo que otros miembros del equipo sepan para qué sirve.

8. (Opcional) Para seleccionar el esquema de nombre predeterminado para las ejecuciones de pruebas, seleccione **Esquema de nombre predeterminado**. Para definir un esquema de nombre propio, seleccione **Esquema definido por el usuario** y, después, escriba el texto que quiera en **Texto de prefijo**. Para anexar la marca de fecha y hora al nombre de la ejecución de pruebas, seleccione **Anexar marca de fecha y hora**.

9. Elija **Roles**.

     Se mostrará la página **Roles**.

     ![Roles de Configuración de pruebas](../test/media/load_testtestrole.png)

10. Para ejecutar las pruebas de manera remota, o para ejecutar las pruebas de manera remota y recopilar datos de manera remota, use la lista desplegable **Método de ejecución de las pruebas** y seleccione **Ejecución remota**.

11. Use la lista desplegable **Controlador** para seleccionar un controlador de pruebas para los agentes de prueba de **Controlador** que se van a usar para ejecutar las pruebas o recopilar datos.

    > [!NOTE]
    > Si es la primera vez que agrega un controlador, no se mostrará ningún controlador en la lista desplegable. Esta lista se rellena con controladores anteriores especificados en otras configuraciones de pruebas. Debe escribir el nombre del controlador en el cuadro (por ejemplo, **TestControllerMachine1**).

12. Para agregar los roles que quiere usar en la ejecución de pruebas y en la recolección de datos, en **Roles**, elija **Agregar**.

13. Escriba un nombre para el rol en la columna **Nombre**. Por ejemplo, el rol podría ser "Servidor web".

14. Repita los pasos 12 y 13 para agregar todos los roles que sean necesarios.

     Cada rol usa un agente de prueba administrado por el controlador de pruebas.

15. Seleccione el rol que quiere usar para ejecutar las pruebas y, después, elija **Establecer como rol para ejecutar pruebas**.

    > [!IMPORTANT]
    > Los demás roles que crea y define no ejecutarán pruebas; solo se usarán para recopilar datos según los adaptadores de datos y diagnóstico que especifique para los roles en la página **Datos y diagnósticos**.

16. Para limitar los agentes que se pueden usar con un rol, seleccione el rol y luego haga clic en **Agregar** en la barra de herramientas situada bajo **Atributos de agente para el rol seleccionado**.

     Se mostrará el cuadro de diálogo **Regla de selección de agentes**.

     Escriba el nombre en **Nombre del atributo** y el valor en **Valor del atributo**; después, elija **Aceptar**. Agregue todos los atributos que necesite.

     Por ejemplo, podría agregar un atributo denominado “RAM > 16GB” que tenga un valor de “True” o “False” para filtrar las máquinas de agente de prueba que tengan más de 16 GB de memoria. Para aplicar el mismo atributo a uno o más agentes de pruebas, use el cuadro de diálogo **Administrar controlador de pruebas**. Para obtener más información, vea [Administrar controladores de pruebas y agentes de pruebas con Visual Studio](../test/manage-test-controllers-and-test-agents.md).

17. Elija **Datos y diagnósticos**.

     Se mostrará la página **Datos y diagnósticos**.

     ![Datos y diagnósticos de Configuración de pruebas](../test/media/load_testtest.png)

18. En la página **Datos y diagnósticos**, defina el rol seleccionando los *adaptadores de datos de diagnóstico* que el rol usará para recopilar datos. Por tanto, si hay uno o más adaptadores de datos y diagnósticos habilitados para el rol, el controlador de pruebas seleccionará un equipo de agente de prueba disponible para recopilar los datos para los adaptadores de datos y diagnósticos especificados basándose en los atributos definidos para el rol. Para seleccionar los datos y los adaptadores de datos de diagnóstico que desea recopilar para cada rol, seleccione el rol. Para cada rol, seleccione los adaptadores de datos de diagnóstico según las necesidades de las pruebas. Si quiere configurar los adaptadores de datos de diagnóstico seleccionados para cada rol, elija **Configurar**.

     **Ejemplo de roles y adaptadores de datos de diagnóstico:**

     Por ejemplo, podría crear un rol de cliente denominado “Cliente de escritorio” que tenga un atributo de “Usa SQL” establecido en “True” y un rol de servidor denominado “SQL Server” que tenga un atributo establecido en “RAM > 16GB”. Si especifica que el “Cliente de escritorio” ejecutará las pruebas eligiendo **Establecer como rol para ejecutar pruebas** en la página **Roles**, el controlador de pruebas seleccionará las máquinas con agentes de prueba que incluyan el atributo “Usa SQL” establecido en “True” en los que ejecutar las pruebas. El controlador de pruebas también seleccionará las máquinas del servidor SQL que tengan agentes de prueba que incluyan el atributo “RAM > 16GB” solo para recopilar los datos definidos por los adaptadores de datos y diagnósticos incluidos en el rol. El agente de prueba "Cliente de escritorio" también puede recopilar datos de los equipos en los que se ejecuta si también selecciona los adaptadores de datos y diagnósticos para ese rol.

     Para obtener información detallada sobre cada adaptador de datos de diagnóstico y cómo configurarlo, vea el tema relacionado que figura en la tabla siguiente.

     Para obtener más información sobre los adaptadores de datos de diagnóstico, vea [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md).

     **Adaptadores de datos de diagnóstico para pruebas de carga**

    |Adaptador de datos de diagnóstico|Uso en pruebas de carga|Tema relacionado|
    |-|-------------------------|-|
    |**Proxy de cliente ASP.NET para IntelliTrace e Impacto en las pruebas:** Este proxy permite recopilar información sobre las llamadas HTTP de un cliente a un servidor web para los adaptadores de datos de diagnóstico de IntelliTrace y de impacto en las pruebas.|![Icono de información](../test/media/vc364f4.gif)<br /><br /> A menos que tenga una necesidad concreta de recopilar información del sistema para los equipos de agente de prueba, no incluya este adaptador. **Precaución:** no se recomienda el uso del adaptador de IntelliTrace en pruebas de carga por los problemas que se producen debido a la gran cantidad de datos que se recopilan. <br /><br /> Los datos de impacto en las pruebas no se recopilan mediante pruebas de carga.||
    |**IntelliTrace:** puede configurar información de seguimiento de diagnóstico específica que se almacena en un archivo de registro. Los archivos de registro tienen la extensión *.tdlog*. Si la ejecución de uno de los pasos de la prueba es incorrecta, puede crear un error. El archivo de registro que contiene el seguimiento de diagnóstico se adjunta automáticamente a este error. Los datos que se recopilan en el archivo de registro aumentan la productividad de la depuración porque reducen el tiempo necesario para reproducir y diagnosticar un error en el código. A partir de este archivo de registro se puede volver a crear la sesión local en otro equipo. Esto reduce el riesgo de que no se pueda reproducir un error.<br /><br /> Para más información, vea [Recopilar datos de IntelliTrace](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md).|![Icono Importante](../test/media/vc364f3.gif)<br /><br /> No se recomienda el uso del adaptador de IntelliTrace en pruebas de carga por los problemas que se producen debido a la gran cantidad de datos que se recopilan y registran. Debe intentar usar el adaptador de IntelliTrace solo en pruebas de carga que no tengan una ejecución prolongada y que no usen muchos agentes de prueba.|[Procedimiento para recopilar datos de IntelliTrace para ayudar a depurar problemas difíciles](../test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues.md)|
    |**Generador de perfiles ASP.NET:** puede crear una configuración de pruebas que incluya la generación de perfiles de ASP.NET, que recopila datos de rendimiento en aplicaciones web ASP.NET.|El adaptador de datos de diagnóstico del generador de perfiles ASP.NET genera perfiles del proceso de Internet Information Services (IIS), por lo que no funcionará en un servidor web de desarrollo. Para generar perfiles del sitio web en su prueba de carga, tiene que instalar un agente de prueba en el equipo en el que se esté ejecutando IIS. El agente de prueba no generará carga, sino que será un agente solo de recopilación. Para obtener más información, vea [Instalar y configurar agentes de prueba](../test/lab-management/install-configure-test-agents.md).|[Cómo: Configurar el generador de perfiles ASP.NET para pruebas de carga mediante la configuración de pruebas](../test/how-to-configure-aspnet-profiler-for-load-tests-using-test-settings.md)|
    |**Registro de eventos:** puede definir una configuración de pruebas para que incluya la recopilación de los registros de eventos, que se incluirá en los resultados de las pruebas.||[Cómo: Configurar la recopilación de registros de eventos mediante la configuración de pruebas](/previous-versions/dd504816(v=vs.110))|
    |**Emulación de red:** puede especificar que quiere colocar una carga de red artificial en la prueba usando una configuración de pruebas. La emulación de la red afecta a la comunicación hacia y desde el equipo, emulando una velocidad de conexión de red determinada, como la conexión de acceso telefónico. **Nota:**  La emulación de la red no se puede usar para aumentar la velocidad de conexión de la red.|Las pruebas de carga omiten el adaptador Emulación de red. En su lugar, las pruebas de carga usan la configuración especificada en la combinación de redes del escenario de prueba de carga.<br /><br /> Para obtener más información, vea [Especificar tipos de redes virtuales en un escenario de prueba de carga](../test/specify-virtual-network-types-in-a-load-test-scenario.md).||
    |**Información del sistema:** se puede establecer una configuración de pruebas para incluir información del sistema sobre los equipos en los que se ejecuta el recopilador de datos y diagnósticos Información del sistema. La información del sistema se especifica en los resultados de pruebas mediante una configuración de pruebas.|![Icono de información](../test/media/vc364f4.gif)<br /><br /> Puede recopilar información del sistema de los agentes de carga y del sistema sometido a prueba.|No es necesaria ninguna configuración para recopilar esta información.|
    |**Impacto en las pruebas:** puede recopilar información sobre los métodos de código de aplicaciones que se usaron al ejecutar un caso de prueba. Dicha información se puede usar junto con los cambios realizados por los desarrolladores en el código de la aplicación para determinar qué pruebas resultaron afectadas por esos cambios de desarrollo.|Las pruebas de carga no recopilan datos de impacto en las pruebas.||
    |**Grabadora de vídeo:** puede crear una grabación de vídeo de su sesión de escritorio mientras ejecuta una prueba automatizada. Esto puede ser útil para ver las acciones del usuario para una prueba de IU codificada. El vídeo puede ayudar a otros miembros del equipo a aislar problemas de la aplicación que son difíciles de reproducir. **Nota:** Cuando se ejecutan pruebas de manera remota, la grabadora de vídeo no funcionará a menos que el agente se ejecute en modo de proceso interactivo.|![Icono de elemento importante](../test/media/vc364f3.gif) **Advertencia:** No se recomienda el uso del adaptador Grabadora de vídeo para las pruebas de carga.|[Procedimiento Incluir grabaciones de la pantalla y de voz durante las pruebas mediante la configuración de pruebas](../test/how-to-include-recordings-of-the-screen-and-voice-during-tests.md)|

19. Elija **Implementación**.

     Se mostrará la página **Implementación**.

20. Para que se cree un directorio de implementación independiente cada vez que ejecute las pruebas, seleccione **Habilitar implementación**.

    > [!NOTE]
    > Si selecciona esta opción, podrá continuar compilando la aplicación cuando ejecute las pruebas.

21. Para agregar un archivo al directorio que está usando para ejecutar las pruebas, elija **Agregar archivo** y, después, seleccione el archivo que quiera agregar.

    > [!NOTE]
    > Al ejecutar una prueba de carga, se implementan automáticamente ensamblados de complementos, archivos de datos y archivos cargados.

22. Para agregar un directorio al directorio que está usando para ejecutar las pruebas, elija **Agregar directorio** y, después, seleccione el directorio que quiera agregar.

23. Para ejecutar los scripts antes y después de las pruebas, elija **Scripts de instalación y limpieza**.

     Aparecerá la página **Scripts de instalación y limpieza**.

    1. Escriba la ubicación del archivo de script en **Script de configuración** o elija los puntos suspensivos (**…**) para buscar el script de configuración.

    2. Escriba la ubicación del archivo de script en **Script de limpieza** o elija los puntos suspensivos (**…**) para buscar el script de limpieza.

24. Para ejecutar las pruebas con un host diferente, elija **Hosts**.

    1. En **Tipo de host**, compruebe que está seleccionado **Predeterminado**.

        > [!NOTE]
        > No se admite **ASP.NET** en **Tipo de host** en las pruebas de carga.

    2. Use la lista desplegable **Ejecutar pruebas en procesos de 32 bits o 64 bits** para seleccionar si quiere que las pruebas unitarias y de rendimiento web de la prueba de carga se ejecuten como procesos de 32 bits o de 64 bits.

        > [!NOTE]
        > Para obtener la máxima flexibilidad, debe compilar los proyectos de prueba de carga y rendimiento web con la configuración **Any CPU** (Cualquier CPU). Después, se pueden ejecutar en ambos agentes de 32 y 64 bits. Compilar proyectos de prueba de carga y rendimiento web con la configuración de **64 bits** no proporciona ninguna ventaja.

25. (Opcional) Para limitar el tiempo de cada serie de pruebas y de cada prueba individual, elija **Tiempos de espera de la prueba**.

    1. Para anular una ejecución de pruebas cuando se supere un límite de tiempo, seleccione **Anular una ejecución de pruebas si su tiempo de ejecución total supera** y, después, escriba un valor para este límite.

    2. Para que se produzca un error en una prueba individual cuando se supere un límite de tiempo, seleccione **Marcar una prueba individual como con errores si su tiempo de ejecución supera** y, después, escriba un valor para este límite.

26. Omita **Prueba unitaria**. Las pruebas de carga no usan estas configuraciones.

27. Omita **Prueba web**. Las pruebas de carga no usan estas configuraciones.

28. Para guardar la configuración de pruebas, elija **Guardar como**. Escriba el nombre del archivo que quiera en **Nombre del objeto**.

## <a name="remove-a-test-settings-file-from-your-solution"></a>Eliminación de un archivo de configuración de pruebas de la solución

En la carpeta **Elementos de la solución** del **Explorador de soluciones**, haga clic con el botón derecho en la configuración de pruebas que quiera quitar y luego elija **Quitar**.

El archivo de la configuración de pruebas se quitará de la solución.

## <a name="see-also"></a>Consulte también

- [Controladores y agentes de prueba](configure-test-agents-and-controllers-for-load-tests.md)
- [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md)