---
title: Guía del administrador de Visual Studio
description: Obtenga más información sobre cómo implementar Visual Studio en un entorno empresarial.
ms.custom: ''
ms.date: 05/29/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0436612d208fa4ffbcc808007849b5d168b049da
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34691123"
---
# <a name="visual-studio-2017-administrator-guide"></a>Guía del administrador de Visual Studio 2017

En entornos empresariales, es habitual que los administradores del sistema implementen instalaciones en los usuarios finales desde un recurso compartido de red o mediante software de administración de sistemas. El motor de instalación de Visual Studio se ha diseñado para admitir implementaciones empresariales, lo que otorga a los administradores del sistema la posibilidad de crear una ubicación de instalación de red, configurar previamente los valores predeterminados de instalación, implementar claves de producto durante el proceso de instalación y administrar actualizaciones de producto después de un lanzamiento satisfactorio. Esta guía de administrador proporciona instrucciones basadas en escenarios para la implementación empresarial en entornos de red.

## <a name="deploy-visual-studio-2017-in-an-enterprise-environment"></a>Implementar Visual Studio 2017 en un entorno empresarial

Puede implementar Visual Studio 2017 en estaciones de trabajo cliente siempre y cuando cada equipo de destino cumpla los [requisitos mínimos de instalación](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs). Tanto si va a realizar la implementación a través de software como System Center o mediante un archivo por lotes, normalmente deberá seguir los pasos siguientes:

1. [Crear un recurso compartido de red que contenga los archivos de producto de Visual Studio](create-a-network-installation-of-visual-studio.md) en una ubicación de red.

2. [Seleccionar las cargas de trabajo y los componentes](workload-and-component-ids.md) que quiere instalar.

3. [Crear un archivo de respuesta](automated-installation-with-response-file.md) que contenga las opciones de instalación predeterminadas. O, como alternativa, [compilar un script de instalación](use-command-line-parameters-to-install-visual-studio.md) que use parámetros de la línea de comandos para controlar la instalación.

4. Opcionalmente, [aplicar una clave de producto de licencia por volumen](automatically-apply-product-keys-when-deploying-visual-studio.md) como parte del script de instalación para que los usuarios no tengan que activar el software por separado.

5. Actualizar el diseño de red para [controlar cuándo se entregan actualizaciones del producto a los usuarios finales](controlling-updates-to-visual-studio-deployments.md).

6. Opcionalmente, establecer las claves del Registro para [controlar lo que se almacena en caché en las áreas de trabajo cliente](set-defaults-for-enterprise-deployments.md).

7. Usar la tecnología de implementación de su elección para ejecutar el script generado en los pasos anteriores en las estaciones de trabajo de destino de los desarrolladores.

8. [Actualizar la ubicación de red con las actualizaciones más recientes](update-a-network-installation-of-visual-studio.md) para Visual Studio mediante la ejecución del comando usado en el paso 1 de forma periódica para agregar componentes actualizados.

> [!IMPORTANT]
> Tenga en cuenta que las instalaciones que se realizan desde un recurso compartido de red "recordarán" la ubicación de la que proceden. Esto significa que, para reparar un equipo cliente, quizás sea necesario volver al recurso compartido de red desde el que se instaló el cliente. Elija cuidadosamente la ubicación de red para que esté disponible durante el tiempo que espera que los clientes de Visual Studio 2017 se ejecuten en su organización.

## <a name="use-visual-studio-tools"></a>Uso de Visual Studio Tools

Tenemos varias herramientas disponibles para ayudarle a [detectar y administrar las instancias de Visual Studio instaladas](tools-for-managing-visual-studio-instances.md) en los equipos cliente.

> [!TIP]
> Además de la documentación de la guía del administrador, una buena fuente de información sobre la instalación de Visual Studio 2017 es el [blog de Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).

## <a name="specify-customer-feedback-settings"></a>Especificar valores de comentarios de clientes

De manera predeterminada, la instalación de Visual Studio permite recibir comentarios de los clientes. Cuando se habilita la directiva de grupo, se puede configurar Visual Studio para deshabilitar los comentarios de los clientes en equipos individuales. Para ello, establezca una directiva basada en el Registro en la siguiente clave:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**

Entry = **OptIn**

Value = (DWORD)
* **0** es no participar
* **1** es participar

Para obtener más información sobre la configuración de los comentarios del cliente, vea la página [Programa para la mejora de la experiencia del usuario de Visual Studio](../ide/visual-studio-experience-improvement-program.md).

## <a name="get-support"></a>Obtener soporte técnico

En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017). Si ninguno de los pasos de solución de problemas ayuda, puede ponerse en contacto con nosotros por chat para obtener asistencia para la instalación (solo en inglés). Para más información, consulte la [página de soporte técnico de Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:

* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto y encontrar respuestas en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/).
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de la [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio). (Esta opción requiere una cuenta de [GitHub](https://github.com/)).

## <a name="see-also"></a>Vea también

* [Instalación de Visual Studio 2017](install-visual-studio.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
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
