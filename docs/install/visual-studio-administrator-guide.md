---
title: Guía del administrador de Visual Studio
titleSuffix: ''
description: Obtenga más información sobre cómo implementar Visual Studio en un entorno empresarial.
ms.date: 06/02/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9a586a0ab0d6b7a3ab34ef581e2ba6f5348232c2
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328796"
---
# <a name="visual-studio-administrator-guide"></a>Guía del administrador de Visual Studio

En entornos empresariales, los administradores de sistemas normalmente implementan instalaciones para los usuarios finales desde un recurso compartido de red o mediante software de administración de sistemas. El motor de instalación de Visual Studio se ha diseñado para admitir implementaciones empresariales, lo que proporciona a los administradores de sistemas la posibilidad de crear una ubicación de instalación de red, de configurar previamente los valores predeterminados de instalación, de implementar claves de producto durante el proceso de instalación y de administrar actualizaciones de producto después de un lanzamiento correcto.

Esta guía de administrador proporciona instrucciones basadas en escenarios para la implementación empresarial en entornos de red.

## <a name="before-you-begin"></a>Antes de empezar

Antes de implementar Visual Studio en la organización, hay algunas decisiones que tomar y varias tareas que realizar:

::: moniker range="vs-2019"

* Asegúrese de que cada equipo de destino cumpla los [requisitos mínimos de instalación](/visualstudio/releases/2019/system-requirements/).

* Decida sobre las necesidades de mantenimiento.

  Si la empresa debe conservar durante más tiempo un conjunto de características pero quiere obtener actualizaciones de mantenimiento periódicas, planee el uso de una base de referencia de mantenimiento. Para más información, consulte la sección ***Opciones de soporte técnico para clientes de las versiones Enterprise y Professional*** de la página [Ciclo de vida y mantenimiento del producto de Visual Studio](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers), así como la página [Procedimiento: Actualización de Visual Studio mientras se encuentra en una base de referencia de mantenimiento](update-servicing-baseline.md).

  Si piensa aplicar las actualizaciones de mantenimiento junto con las actualizaciones acumulativas de características, puede elegir las más recientes.

* Decida sobre el modelo de actualización.

  ¿Dónde quiere que los equipos cliente individuales obtengan las actualizaciones? En concreto, decida si quiere obtener actualizaciones desde Internet o desde un recurso compartido local de la empresa. Luego, si opta por usar un recurso compartido local, decida si los usuarios individuales pueden actualizar sus propios clientes o si quiere que un administrador actualice los clientes mediante programación.

* Decida qué [cargas de trabajo y componentes](workload-and-component-ids.md?view=vs-2019) necesita la empresa.

* Decida si se va a usar un [archivo de respuesta](automated-installation-with-response-file.md?view=vs-2019) (que simplifica la administración de detalles en el archivo de script).

* Decida si quiere habilitar la directiva de grupo y si quiere configurar Visual Studio para deshabilitar los comentarios de los clientes en equipos individuales.

::: moniker-end

::: moniker range="vs-2017"

* Asegúrese de que cada equipo de destino cumpla los [requisitos mínimos de instalación](/visualstudio/productinfo/vs2017-system-requirements-vs/).

* Decida sobre las necesidades de mantenimiento.

  Si la empresa debe conservar durante más tiempo un conjunto de características pero quiere obtener actualizaciones de mantenimiento periódicas, planee el uso de una base de referencia de mantenimiento. Para más información, consulte la sección ***Soporte técnico de versiones anteriores de Visual Studio*** de la página [Ciclo de vida y mantenimiento del producto de Visual Studio](/visualstudio/releases/2019/servicing#support-for-older-versions-of-visual-studio), así como la página [Procedimiento: Actualización de Visual Studio mientras se encuentra en una base de referencia de mantenimiento](update-servicing-baseline.md).

  Si piensa aplicar las actualizaciones de mantenimiento junto con las actualizaciones acumulativas de características, puede elegir las más recientes.

* Decida sobre el modelo de actualización.

  ¿Dónde quiere que los equipos cliente individuales obtengan las actualizaciones? En concreto, decida si quiere obtener actualizaciones desde Internet o desde un recurso compartido local de la empresa. Luego, si opta por usar un recurso compartido local, decida si los usuarios individuales pueden actualizar sus propios clientes o si quiere que un administrador actualice los clientes mediante programación.

* Decida qué [cargas de trabajo y componentes](workload-and-component-ids.md?view=vs-2017) necesita la empresa.

* Decida si se va a usar un [archivo de respuesta](automated-installation-with-response-file.md?view=vs-2017) (que simplifica la administración de detalles en el archivo de script).

* Decida si quiere habilitar la directiva de grupo y si quiere configurar Visual Studio para deshabilitar los comentarios de los clientes en equipos individuales.

::: moniker-end

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Paso 1: Descargar archivos de producto de Visual Studio

* [Seleccione las cargas de trabajo y los componentes](workload-and-component-ids.md?view=vs-2019) que quiere instalar.

* [Cree un recurso compartido de red para los archivos de producto de Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2019).

## <a name="step-2---build-an-installation-script"></a>Paso 2: Crear un script de instalación

* Cree un script de instalación que use [parámetros de línea de comandos](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019) para controlar la instalación.

  >[!NOTE]
  > Puede simplificar los scripts mediante un [archivo de respuesta](automated-installation-with-response-file.md?view=vs-2019). Asegúrese de crear un archivo de respuesta que contenga la opción de instalación predeterminada.

* (Opcional) [Aplique una clave de producto de licencia por volumen](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019) como parte del script de instalación para que los usuarios no tengan que activar el software por separado.

* (Opcional) Actualice el diseño de red para [controlar cuándo y dónde se entregan las actualizaciones de producto a los usuarios finales](controlling-updates-to-visual-studio-deployments.md?view=vs-2019).

* (Opcional) Establezca directivas del Registro que afecten a la implementación de Visual Studio, por ejemplo, dónde se instalan algunos paquetes compartidos con otras versiones o instancias, [dónde se almacenan en caché los paquetes](set-defaults-for-enterprise-deployments.md?view=vs-2019) o [si los paquetes se almacenan en caché](disable-or-move-the-package-cache.md?view=vs-2019).

* (Opcional) Establezca la directiva de grupo. También puede [configurar Visual Studio para deshabilitar los comentarios de los clientes](../ide/visual-studio-experience-improvement-program.md) en equipos individuales.

## <a name="step-3---deploy"></a>Paso 3: Implementar

* Use la tecnología de implementación que prefiera para ejecutar el script en las estaciones de trabajo de destino de los desarrolladores.

## <a name="step-4---deploy-updates"></a>Paso 4: Implementar actualizaciones

* [Actualizar la ubicación de red con las actualizaciones más recientes](update-a-network-installation-of-visual-studio.md?view=vs-2019) para Visual Studio mediante la ejecución del comando usado en el paso 1 de forma periódica para agregar componentes actualizados.

  Puede actualizar Visual Studio mediante un script de actualización. Para ello, use el parámetro de línea de comandos [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019).

## <a name="step-5---optional-use-visual-studio-tools"></a>Paso 5: (Opcional) Usar Visual Studio Tools

Tenemos varias herramientas disponibles para ayudarle a [detectar y administrar las instancias de Visual Studio instaladas](tools-for-managing-visual-studio-instances.md?view=vs-2019) en los equipos cliente.

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Paso 1: Descargar archivos de producto de Visual Studio

* [Seleccione las cargas de trabajo y los componentes](workload-and-component-ids.md?view=vs-2017) que quiere instalar.

* [Cree un recurso compartido de red para los archivos de producto de Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2017).

## <a name="step-2---build-an-installation-script"></a>Paso 2: Crear un script de instalación

* Cree un script de instalación que use [parámetros de línea de comandos](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017) para controlar la instalación.

  >[!NOTE]
  > Puede simplificar los scripts mediante un [archivo de respuesta](automated-installation-with-response-file.md?view=vs-2017). Asegúrese de crear un archivo de respuesta que contenga la opción de instalación predeterminada.

* (Opcional) [Aplique una clave de producto de licencia por volumen](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017) como parte del script de instalación para que los usuarios no tengan que activar el software por separado.

* (Opcional) Actualice el diseño de red para [controlar cuándo y dónde se entregan las actualizaciones de producto a los usuarios finales](controlling-updates-to-visual-studio-deployments.md?view=vs-2017).

* (Opcional) Establezca directivas del Registro que afecten a la implementación de Visual Studio, por ejemplo, dónde se instalan algunos paquetes compartidos con otras versiones o instancias, [dónde se almacenan en caché los paquetes](set-defaults-for-enterprise-deployments.md?view=vs-2019) o [si los paquetes se almacenan en caché](disable-or-move-the-package-cache.md?view=vs-2017).

* (Opcional) Establezca la directiva de grupo. También puede [configurar Visual Studio para deshabilitar los comentarios de los clientes](../ide/visual-studio-experience-improvement-program.md) en equipos individuales.

## <a name="step-3---deploy"></a>Paso 3: Implementar

* Use la tecnología de implementación que prefiera para ejecutar el script en las estaciones de trabajo de destino de los desarrolladores.

## <a name="step-4---deploy-updates"></a>Paso 4: Implementar actualizaciones

* [Actualizar la ubicación de red con las actualizaciones más recientes](update-a-network-installation-of-visual-studio.md?view=vs-2017) para Visual Studio mediante la ejecución del comando usado en el paso 1 de forma periódica para agregar componentes actualizados.

  Puede actualizar Visual Studio mediante un script de actualización. Para ello, use el parámetro de línea de comandos [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019).

## <a name="step-5---optional-use-visual-studio-tools"></a>Paso 5: (Opcional) Usar Visual Studio Tools

Tenemos varias herramientas disponibles para ayudarle a [detectar y administrar las instancias de Visual Studio instaladas](tools-for-managing-visual-studio-instances.md?view=vs-2017) en los equipos cliente.

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Ejemplos de parámetros de línea de comandos](command-line-parameter-examples.md)
* [Instalar los certificados necesarios para la instalación sin conexión de Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Importación o exportación de configuraciones de instalación](import-export-installation-configurations.md)
* [Archivos de instalación de Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Ciclo de vida y mantenimiento del producto de Visual Studio](/visualstudio/releases/2019/servicing/)
* [Extensiones cargadas automáticamente y sincrónicamente](../extensibility/synchronously-autoloaded-extensions.md)
