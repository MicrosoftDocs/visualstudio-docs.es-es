---
title: Guía del administrador de Visual Studio
titleSuffix: ''
description: Obtenga más información sobre cómo implementar Visual Studio en un entorno empresarial.
ms.date: 05/29/2018
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
ms.openlocfilehash: c9dbd7c3687596df0ccb0397cc5d52ff7888f9ff
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2019
ms.locfileid: "58324940"
---
# <a name="visual-studio-administrator-guide"></a>Guía del administrador de Visual Studio

En entornos empresariales, es habitual que los administradores del sistema implementen instalaciones en los usuarios finales desde un recurso compartido de red o mediante software de administración de sistemas. El motor de instalación de Visual Studio se ha diseñado para admitir implementaciones empresariales, lo que otorga a los administradores del sistema la posibilidad de crear una ubicación de instalación de red, configurar previamente los valores predeterminados de instalación, implementar claves de producto durante el proceso de instalación y administrar actualizaciones de producto después de un lanzamiento satisfactorio. Esta guía de administrador proporciona instrucciones basadas en escenarios para la implementación empresarial en entornos de red.

## <a name="deploy-visual-studio-in-an-enterprise-environment"></a>Implementación de Visual Studio en un entorno empresarial

Puede implementar Visual Studio en estaciones de trabajo cliente siempre y cuando cada equipo de destino cumpla los [requisitos mínimos de instalación](/visualstudio/productinfo/vs2017-system-requirements-vs). Tanto si va a realizar la implementación a través de software como System Center o mediante un archivo por lotes, normalmente deberá seguir los pasos siguientes:

1. [Crear un recurso compartido de red que contenga los archivos de producto de Visual Studio](create-a-network-installation-of-visual-studio.md) en una ubicación de red.

2. [Seleccionar las cargas de trabajo y los componentes](workload-and-component-ids.md) que quiere instalar.

3. [Crear un archivo de respuesta](automated-installation-with-response-file.md) que contenga las opciones de instalación predeterminadas. O, como alternativa, [compilar un script de instalación](use-command-line-parameters-to-install-visual-studio.md) que use parámetros de la línea de comandos para controlar la instalación.

4. Opcionalmente, [aplicar una clave de producto de licencia por volumen](automatically-apply-product-keys-when-deploying-visual-studio.md) como parte del script de instalación para que los usuarios no tengan que activar el software por separado.

5. Actualizar el diseño de red para [controlar cuándo se entregan actualizaciones del producto a los usuarios finales](controlling-updates-to-visual-studio-deployments.md).

6. Opcionalmente, establecer las claves del Registro para [controlar lo que se almacena en caché en las áreas de trabajo cliente](set-defaults-for-enterprise-deployments.md).

7. Usar la tecnología de implementación de su elección para ejecutar el script generado en los pasos anteriores en las estaciones de trabajo de destino de los desarrolladores.

8. [Actualizar la ubicación de red con las actualizaciones más recientes](update-a-network-installation-of-visual-studio.md) para Visual Studio mediante la ejecución del comando usado en el paso 1 de forma periódica para agregar componentes actualizados.

> [!IMPORTANT]
> Tenga en cuenta que las instalaciones que se realizan desde un recurso compartido de red "recordarán" la ubicación de la que proceden. Esto significa que, para reparar un equipo cliente, quizás sea necesario volver al recurso compartido de red desde el que se instaló el cliente. Elija cuidadosamente la ubicación de red para que esté disponible durante el tiempo que espera que los clientes de Visual Studio se ejecuten en su organización.

## <a name="use-visual-studio-tools"></a>Uso de Visual Studio Tools

Tenemos varias herramientas disponibles para ayudarle a [detectar y administrar las instancias de Visual Studio instaladas](tools-for-managing-visual-studio-instances.md) en los equipos cliente.

> [!TIP]
> Además de la documentación de la guía del administrador, una buena fuente de información sobre la instalación de Visual Studio es [Visual Studio Setup Archives](https://devblogs.microsoft.com/setup/tag/vs2017/) (Archivos de instalación de Visual Studio).

## <a name="specify-customer-feedback-settings"></a>Especificar valores de comentarios de clientes

De manera predeterminada, la instalación de Visual Studio permite recibir comentarios de los clientes. Cuando se habilita la directiva de grupo, se puede configurar Visual Studio para deshabilitar los comentarios de los clientes en equipos individuales. Para ello, establezca una directiva basada en el Registro en la siguiente clave:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**

Entry = **OptIn**

Value = (DWORD)
* **0** es no participar
* **1** es participar

Para obtener más información sobre la configuración de los comentarios del cliente, vea la página [Programa para la mejora de la experiencia del usuario de Visual Studio](../ide/visual-studio-experience-improvement-program.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vea también

* [Instalar Visual Studio](install-visual-studio.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Ejemplos de parámetros de línea de comandos](command-line-parameter-examples.md)
  * [Carga de trabajo y referencia de id. de componente](workload-and-component-ids.md)
* [Crear una instalación basada en red de Visual Studio](create-a-network-installation-of-visual-studio.md)
  * [Instalar los certificados necesarios para la instalación sin conexión de Visual Studio](install-certificates-for-visual-studio-offline.md)
* [Automatizar Visual Studio con un archivo de respuesta](automated-installation-with-response-file.md)
* [Aplicar automáticamente las claves de producto durante la implementación de Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [Establecer valores predeterminados para implementaciones empresariales de Visual Studio](set-defaults-for-enterprise-deployments.md)
* [Deshabilitar o mover la caché del paquete](disable-or-move-the-package-cache.md)
* [Actualizar una instalación basada en red de Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Controlar las actualizaciones a implementaciones de Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Herramientas para detectar y administrar instancias de Visual Studio](tools-for-managing-visual-studio-instances.md)
