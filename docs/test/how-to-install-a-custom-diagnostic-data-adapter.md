---
title: 'Cómo: Instalar un adaptador de datos de diagnóstico personalizado en Visual Studio'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter, installing
ms.assetid: 907e65d8-0408-44b3-9e5e-e631892c1726
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: d24ce9f954164cd8d243edfab4387f6b174c0648
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31968541"
---
# <a name="how-to-install-a-custom-diagnostic-data-adapter"></a>Cómo: Instalar un adaptador de datos de diagnóstico personalizado

Si ha creado un adaptador de datos de diagnóstico personalizado o se le ha proporcionado uno, puede instalar su ensamblado de adaptador de datos de diagnóstico copiando el archivo de ensamblado correspondiente en el directorio correcto del equipo local.

 Si desea usar su adaptador de datos de diagnóstico personalizado para un rol en un entorno, debe instalarlo en todos los equipos que ejecutan los agentes de prueba que se pueden usar para este rol.

 Use el procedimiento siguiente para instalar el adaptador de diagnóstico personalizado en las ubicaciones adecuadas. Necesitará permisos administrativos en cualquier equipo donde instale el adaptador de datos de diagnóstico.

## <a name="installing-a-custom-diagnostic-data-adapter"></a>Instalar un adaptador de datos de diagnóstico personalizado

### <a name="to-install-a-custom-diagnostic-data-adapter"></a>Para instalar un adaptador de datos de diagnóstico personalizado

1.  Copie todos los archivos del directorio de compilación en el siguiente directorio del equipo de destino, según la ruta de instalación, para utilizar el adaptador de datos de diagnóstico cuando haga pruebas en el equipo cliente o en un equipo del agente:

     *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies\DataCollectors*

     Archivos que se van a copiar:

    -   Ensamblado (.dll) del adaptador de datos de diagnóstico (necesario).

    -   Archivo de datos de depuración (.pdb) del adaptador (opcional).

    -   Archivo de configuración del adaptador (`<diagnostic data adapter name>.dll.config`), si los valores de configuración son los predeterminados (opcional).

    -   Ensamblado del editor de configuración, si ha creado uno para editar la configuración del adaptador (opcional). Solo afecta a los equipos cliente. Los equipos del agente no utilizan el editor.

    > [!NOTE]
    > Aunque el adaptador de datos de diagnóstico y el editor de configuración se pueden crear en el mismo proyecto y compilar en el mismo ensamblado, si lo prefiere puede utilizar proyectos independientes y crear ensamblados independientes para ellos.

     Para obtener más información sobre cómo establecer la configuración de pruebas para usar un entorno al ejecutar las pruebas, vea [Recopilar datos de diagnóstico en pruebas manuales (VSTS)](/vsts/manual-test/mtm/collect-more-diagnostic-data-in-manual-tests).

2.  Para seleccionar el adaptador de datos de diagnóstico para una prueba, antes debe seleccionar una configuración de pruebas existente o bien crear una nueva en Microsoft Test Manager o en Visual Studio. Luego, seleccione el adaptador de datos de diagnóstico en la pestaña **Datos y diagnósticos** de la configuración de pruebas seleccionada.

3.  Si ha creado e instalado un editor de configuración del adaptador de datos de diagnóstico, si quiere ajustarlo para su configuración de pruebas, elija **Configurar** junto al adaptador y realice las modificaciones oportunas. Después, elija **Guardar**. Para más información sobre cómo crear un editor de configuración para el recopilador de datos de diagnóstico, vea [Cómo: Crear un editor personalizado para los datos del adaptador de datos de diagnóstico](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md).

4.  Si va a ejecutar las pruebas en Microsoft Test Manager, antes de ello puede asignar esta configuración de pruebas al plan de pruebas o usar el comando **Ejecutar con opciones** para asignar e invalidar la configuración de pruebas. Para obtener más información sobre la configuración de pruebas, vea [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md).

     Si ejecuta las pruebas desde Visual Studio, debe establecer que esta configuración de pruebas esté activa. Para obtener más información sobre la configuración de pruebas, vea [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md).

5.  Ejecute las pruebas usando la configuración de pruebas y con el adaptador de datos de diagnóstico seleccionado.

## <a name="see-also"></a>Vea también

- [Cómo: Crear un adaptador de datos de diagnóstico](../test/how-to-create-a-diagnostic-data-adapter.md)
- [Cómo: Crear un editor personalizado para los datos del adaptador de datos de diagnóstico](../test/how-to-create-a-custom-editor-for-data-for-your-diagnostic-data-adapter.md)
- [Proyecto de ejemplo para crear un adaptador de datos de diagnóstico](../test/sample-project-for-creating-a-diagnostic-data-adapter.md)
- [Crear un adaptador de datos de diagnóstico para recopilar datos personalizados o afectar a un equipo de prueba](../test/create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine.md)
- [Recopilar información de diagnóstico con la configuración de pruebas](../test/collect-diagnostic-information-using-test-settings.md)