---
title: Guía del administrador de Visual Studio
titleSuffix: ''
description: Obtenga más información sobre cómo implementar Visual Studio en un entorno empresarial.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: overview
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0b86d8bc6d3533d2ed50eb4e87330a81f1028f13
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547419"
---
# <a name="visual-studio-administrator-guide"></a>Guía del administrador de Visual Studio

En entornos empresariales, los administradores de sistemas normalmente implementan instalaciones en los usuarios finales desde un recurso compartido de red o mediante software de administración de sistemas. El motor de instalación de Visual Studio se ha diseñado para admitir implementaciones empresariales, lo que proporciona a los administradores de sistemas la posibilidad de crear una ubicación de instalación de red, de configurar previamente los valores predeterminados de instalación, de implementar claves de producto durante el proceso de instalación y de administrar actualizaciones de producto después de un lanzamiento correcto.

Esta guía de administrador proporciona instrucciones basadas en escenarios para la implementación empresarial en entornos de red.

## <a name="before-you-begin"></a>Antes de empezar

Antes de implementar Visual Studio en la organización, hay algunas decisiones que tomar y varias tareas que realizar:

::: moniker range="vs-2019"

* Asegúrese de que cada equipo de destino cumpla los [requisitos mínimos de instalación](/visualstudio/releases/2019/system-requirements/).

::: moniker-end

::: moniker range="vs-2017"

* Asegúrese de que cada equipo de destino cumpla los [requisitos mínimos de instalación](/visualstudio/productinfo/vs2017-system-requirements-vs/).

::: moniker-end

* Decida sobre las necesidades de mantenimiento.

  Si la empresa debe conservar durante más tiempo un conjunto de características pero quiere obtener actualizaciones de mantenimiento periódicas, planee el uso de una base de referencia de mantenimiento. Para más información, consulte la sección ***Opciones de soporte técnico para clientes de las versiones Enterprise y Professional*** de la página [Ciclo de vida y mantenimiento del producto de Visual Studio](/visualstudio/releases/2019/servicing#support-options-for-enterprise-and-professional-customers), así como la página [Actualización de Visual Studio mientras se encuentra en una base de referencia de mantenimiento](update-servicing-baseline.md).

* Decida sobre el modelo de actualización.

  ¿De dónde quiere que las máquinas cliente individuales obtengan las actualizaciones de productos? En concreto, decida si quiere que el cliente obtenga actualizaciones de Internet o de un recurso compartido local de la empresa. Luego, si opta por usar un recurso compartido local, decida si los usuarios individuales pueden actualizar sus propios clientes o si quiere que un administrador actualice los clientes mediante programación. Es mejor que estas decisiones se realicen antes de que se produzca la instalación original en la máquina cliente. Para obtener más información, consulte [Crear una instalación sin conexión de Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md).

  Se puede actualizar un diseño de instalación de red de Visual Studio con las actualizaciones de producto más recientes, de manera que se puede usar tanto como punto de instalación de la actualización más reciente de Visual Studio como para mantener instalaciones que ya están implementadas en estaciones de trabajo cliente. Para obtener más información, consulte [Actualización de una instalación basada en red de Visual Studio](../install/update-a-network-installation-of-visual-studio.md).

  Las organizaciones que usan herramientas de implementación de empresa pueden aprovechar el hecho de que las actualizaciones de Visual Studio están disponibles en el Catálogo de Microsoft Update y Windows Server Update Services. Para más información, consulte [Habilitación de actualizaciones de administrador](../install/enabling-administrator-updates.md) y [Aplicación de actualizaciones de administrador](../install/applying-administrator-updates.md).

  En el caso de los equipos que no están conectados a Internet, la creación de un diseño mínimo es la manera más fácil y rápida de actualizar las instancias de Visual Studio sin conexión. Para obtener más información, consulte [Actualización de Visual Studio con un diseño sin conexión mínimo](update-minimal-layout.md).

::: moniker range="vs-2019"

* Decida qué [cargas de trabajo y componentes](workload-and-component-ids.md?view=vs-2019&preserve-view=true) necesita la empresa.

* Decida si se va a usar un [archivo de respuesta](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true) (que simplifica la administración de detalles en el archivo de script).

::: moniker-end

::: moniker range="vs-2017"

* Decida qué [cargas de trabajo y componentes](workload-and-component-ids.md?view=vs-2017&preserve-view=true) necesita la empresa.

* Decida si se va a usar un [archivo de respuesta](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true) (que simplifica la administración de detalles en el archivo de script).

::: moniker-end

* Decida si quiere habilitar la directiva de grupo y si quiere configurar Visual Studio para deshabilitar los comentarios de los clientes en equipos individuales.

::: moniker range="vs-2019"

## <a name="step-1---download-visual-studio-product-files"></a>Paso 1: Descargar archivos de producto de Visual Studio

* [Seleccione las cargas de trabajo y los componentes](workload-and-component-ids.md?view=vs-2019&preserve-view=true) que quiere instalar.

* [Cree un recurso compartido de red para los archivos de producto de Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Paso 2: Crear un script de instalación

* Cree un script de instalación que use [parámetros de línea de comandos](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true) para controlar la instalación.

  >[!NOTE]
  > Puede simplificar los scripts mediante un [archivo de respuesta](automated-installation-with-response-file.md?view=vs-2019&preserve-view=true). Asegúrese de crear un archivo de respuesta que contenga la opción de instalación predeterminada.

* (Opcional) [Aplique una clave de producto de licencia por volumen](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2019&preserve-view=true) como parte del script de instalación para que los usuarios no tengan que activar el software por separado.

* (Opcional) Actualice el diseño de red para [controlar cuándo y desde dónde se entregan las actualizaciones de producto a los usuarios finales](controlling-updates-to-visual-studio-deployments.md?view=vs-2019&preserve-view=true).

* (Opcional) Establezca directivas del Registro que afecten a la implementación de Visual Studio, por ejemplo, dónde se instalan algunos paquetes compartidos con otras versiones o instancias, [dónde se almacenan en caché los paquetes](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true) o [si los paquetes se almacenan en caché](disable-or-move-the-package-cache.md?view=vs-2019&preserve-view=true).

* (Opcional) Establezca la directiva de grupo. También puede [configurar Visual Studio para deshabilitar los comentarios de los clientes](../ide/visual-studio-experience-improvement-program.md) en equipos individuales.

## <a name="step-3---deploy-updates"></a>Paso 3: Implementación de actualizaciones

Use la tecnología de implementación que prefiera para ejecutar el script en las estaciones de trabajo de destino de los desarrolladores.

* [Actualizar la ubicación de red con las actualizaciones más recientes](update-a-network-installation-of-visual-studio.md?view=vs-2019&preserve-view=true) para Visual Studio mediante la ejecución del comando usado en el paso 1 de forma periódica para agregar componentes actualizados.

  Puede actualizar Visual Studio mediante un script de actualización. Para ello, use el parámetro de línea de comandos [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true).

  Puede implementar actualizaciones de Visual Studio desde Windows Server Update Services o el Catálogo de Microsoft Update con herramientas como System Center Configuration Manager.  Para más información, consulte [Aplicación de actualizaciones de administrador](applying-administrator-updates.md). 

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>Paso 4 (opcional): Uso de Visual Studio Tools para comprobar la instalación

Tenemos varias herramientas disponibles para ayudarle a [detectar y administrar las instancias de Visual Studio instaladas](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true) en los equipos cliente.

## <a name="advanced-configuration"></a>Configuración avanzada

De forma predeterminada, la instalación de Visual Studio permite la inclusión de tipos personalizados en las búsquedas de Bing desde la lista de errores F1 y los vínculos de código. Puede configurar Visual Studio para deshabilitar el mecanismo de búsqueda e impedir la inclusión de cualquier tipo de usuario personalizado cambiando el valor de la siguiente clave del Registro por una directiva:

**"PutCustomTypeInBingSearch" DWORD 0**

El registro se encuentra en el directorio *Software\Microsoft\VisualStudio\16.0_{InstanceId}\Roslyn\Internal\Diagnostics\* del subárbol de su Registro privado. Para obtener instrucciones sobre cómo abrir el subárbol del Registro, consulte la sección [Edición del Registro para una instancia de Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2019&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

::: moniker range="vs-2017"

## <a name="step-1---download-visual-studio-product-files"></a>Paso 1: Descargar archivos de producto de Visual Studio

* [Seleccione las cargas de trabajo y los componentes](workload-and-component-ids.md?view=vs-2017&preserve-view=true) que quiere instalar.

* [Cree un recurso compartido de red para los archivos de producto de Visual Studio](create-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true).

## <a name="step-2---build-an-installation-script"></a>Paso 2: Crear un script de instalación

* Cree un script de instalación que use [parámetros de línea de comandos](use-command-line-parameters-to-install-visual-studio.md?view=vs-2017&preserve-view=true) para controlar la instalación.

  >[!NOTE]
  > Puede simplificar los scripts mediante un [archivo de respuesta](automated-installation-with-response-file.md?view=vs-2017&preserve-view=true). Asegúrese de crear un archivo de respuesta que contenga la opción de instalación predeterminada.

* (Opcional) [Aplique una clave de producto de licencia por volumen](automatically-apply-product-keys-when-deploying-visual-studio.md?view=vs-2017&preserve-view=true) como parte del script de instalación para que los usuarios no tengan que activar el software por separado.

* (Opcional) Actualice el diseño de red para [controlar cuándo y desde dónde se entregan las actualizaciones de producto a los usuarios finales](controlling-updates-to-visual-studio-deployments.md?view=vs-2017&preserve-view=true).

* (Opcional) Establezca directivas del Registro que afecten a la implementación de Visual Studio, por ejemplo, dónde se instalan algunos paquetes compartidos con otras versiones o instancias, [dónde se almacenan en caché los paquetes](set-defaults-for-enterprise-deployments.md?view=vs-2019&preserve-view=true) o [si los paquetes se almacenan en caché](disable-or-move-the-package-cache.md?view=vs-2017&preserve-view=true).

* (Opcional) Establezca la directiva de grupo. También puede [configurar Visual Studio para deshabilitar los comentarios de los clientes](../ide/visual-studio-experience-improvement-program.md) en equipos individuales.

## <a name="step-3---deploy-updates"></a>Paso 3: Implementación de actualizaciones

Use la tecnología de implementación que prefiera para ejecutar el script en las estaciones de trabajo de destino de los desarrolladores.

* [Actualizar la ubicación de red con las actualizaciones más recientes](update-a-network-installation-of-visual-studio.md?view=vs-2017&preserve-view=true) para Visual Studio mediante la ejecución del comando usado en el paso 1 de forma periódica para agregar componentes actualizados.

  Puede actualizar Visual Studio mediante un script de actualización. Para ello, use el parámetro de línea de comandos [`update`](use-command-line-parameters-to-install-visual-studio.md?view=vs-2019&preserve-view=true).

  Puede implementar actualizaciones de Visual Studio desde Windows Server Update Services o el Catálogo de Microsoft Update con herramientas como System Center Configuration Manager. Para más información, consulte [Aplicación de actualizaciones de administrador](applying-administrator-updates.md).

## <a name="step-4---optional-use-visual-studio-tools-to-verify-installation"></a>Paso 4 (opcional): Uso de Visual Studio Tools para comprobar la instalación

Tenemos varias herramientas disponibles para ayudarle a [detectar y administrar las instancias de Visual Studio instaladas](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true) en los equipos cliente.

## <a name="advanced-configuration"></a>Configuración avanzada

De forma predeterminada, la instalación de Visual Studio permite la inclusión de tipos personalizados en las búsquedas de Bing desde la lista de errores F1 y los vínculos de código. Puede configurar Visual Studio para deshabilitar el mecanismo de búsqueda e impedir la inclusión de cualquier tipo de usuario personalizado cambiando el valor de la siguiente clave del Registro por una directiva:

**"PutCustomTypeInBingSearch" DWORD 0**

El registro se encuentra en el directorio `Software\Microsoft\VisualStudio\15.0_{InstanceId}\Roslyn\Internal\Diagnostics\` del subárbol del Registro privado. Para obtener instrucciones sobre cómo abrir el subárbol del Registro, consulte la sección [Edición del Registro para una instancia de Visual Studio](tools-for-managing-visual-studio-instances.md?view=vs-2017&preserve-view=true#editing-the-registry-for-a-visual-studio-instance).

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Consulte también

* [Habilitación de las actualizaciones de administrador](enabling-administrator-updates.md)
* [Aplicación de las actualizaciones de administrador](applying-administrator-updates.md)
* [Ejemplos de parámetros de línea de comandos](command-line-parameter-examples.md)
* [Instalar los certificados necesarios para la instalación sin conexión de Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Importación o exportación de configuraciones de instalación](import-export-installation-configurations.md)
* [Archivos de instalación de Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/)
* [Ciclo de vida y mantenimiento del producto de Visual Studio](/visualstudio/releases/2019/servicing/)
* [Extensiones cargadas automáticamente y sincrónicamente](../extensibility/synchronously-autoloaded-extensions.md)
