---
title: Referencia de las opciones de Cuentas
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.RoamingSettings
ms.assetid: 3cfe09d2-1120-46e8-b882-f7056acb778b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00b99a75579f63dd19de74c6d5bc3c13a2833bc3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996124"
---
# <a name="accounts-environment-options-dialog-box"></a>Cuentas, Entorno, Opciones (Cuadro de diálogo)

Utilice esta página para establecer diversas opciones relacionadas con las cuentas que se usan para iniciar sesión en Visual Studio.

## <a name="personalization-account"></a>Cuenta de personalización

### <a name="synchronize-settings-across-devices"></a>Sincronizar la configuración de los dispositivos

Use esta opción para especificar si se va a sincronizar la configuración en varios equipos. Para obtener más información, vea [Configuración sincronizada](../../ide/synchronized-settings-in-visual-studio.md).

### <a name="enable-device-code-flow"></a>Habilitar flujo de código del dispositivo

Si se selecciona esta opción, el comportamiento de Visual Studio cambia cuando se selecciona **Agregar una cuenta** en la página **Archivo** > **Configuración de la cuenta**. En lugar de ver la página **Iniciar sesión en la cuenta**, aparecerá un cuadro de diálogo con una dirección URL y un código para pegarlos en un explorador web para iniciar sesión. Esta opción es útil en casos donde no se puede iniciar sesión en Visual Studio de la forma habitual, por ejemplo, si usa una versión anterior de Internet Explorer, o si el firewall restringe el acceso. Para obtener más información, vea [Trabajar con varias cuentas de usuario](../work-with-multiple-user-accounts.md#add-an-account-using-device-code-flow).

## <a name="registered-azure-clouds"></a>Nubes de Azure registradas

Esta sección muestra las instancias de nube de Azure a las que el usuario accede mediante una o varias de las cuentas que usa para iniciar sesión en Visual Studio. Por ejemplo, podría tener acceso a una instancia privada de Azure en el centro de datos de su compañía, o puede que tenga acceso a una instancia soberana o gubernamental de Azure, como Azure en China o Azure Gobierno de EE.UU. La instancia de nube de Azure global aparece de forma predeterminada en la lista y se no puede quitar.

Registre una nube de Azure adicional seleccionando el botón **Agregar**. El cuadro de diálogo **Agregar nueva nube de Azure** muestra las distintas instancias de nube de Azure conocidas a las que se puede conectar, aunque también puede escribir la dirección URL de un punto de conexión de Azure privado.

![Agregar nueva instancia de nube de Azure](media/add-new-azure-cloud.png)

Tras registrar una nube de Azure adicional, puede elegir en qué nube de Azure quiere iniciar sesión cuando inicie sesión en Visual Studio.

## <a name="see-also"></a>Vea también

- [Sincronizar la configuración de Visual Studio en varios equipos](../synchronized-settings-in-visual-studio.md)
- [Inicio de sesión en Visual Studio](../signing-in-to-visual-studio.md)
- [Trabajar con varias cuentas de usuario](../work-with-multiple-user-accounts.md)
- [Configuración del entorno](../environment-settings.md)
- [Opciones de entorno (Cuadro de diálogo)](../../ide/reference/environment-options-dialog-box.md)