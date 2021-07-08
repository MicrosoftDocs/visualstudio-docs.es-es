---
title: Experiencias conectadas en Visual Studio
description: Una experiencia conectada se conecta a Internet desde una máquina cliente y proporciona un servicio al cliente.
ms.date: 05/20/2021
ms.topic: conceptual
helpviewer_keywords: ''
author: SayyedaM
ms.author: sayyedamussa
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.openlocfilehash: 689fc40be8aee959023777a3fac6d9134ee979ea
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2021
ms.locfileid: "113222895"
---
# <a name="connected-experiences-in-visual-studio"></a>**Experiencias conectadas en Visual Studio** #

Visual Studio consta de aplicaciones de software cliente y experiencias conectadas diseñadas para permitirle programar de forma más eficaz. La actualización de un paquete [NuGet](/nuget/consume-packages/install-use-packages-visual-studio), la selección de una sugerencia de [IntelliCode](/visualstudio/intellicode/overview) y la colaboración con otro desarrollador mediante [Live Share](/visualstudio/liveshare/quickstart/share) son ejemplos de experiencias conectadas. 

## <a name="choose-whether-these-connected-experiences-are-available-to-use"></a>Elija si estas experiencias conectadas están disponibles para su uso. ##

Puede elegir qué experiencias conectadas usar. Para usar determinadas experiencias conectadas se necesita un contrato con términos diferentes y adicionales a los del CLUF de Visual Studio. Estas experiencias pueden ser servicios en línea propiedad de Microsoft o servicios propiedad de terceros. Por ejemplo, cuando se usan experiencias conectadas de GitHub, se aplicarán la [Declaración de privacidad de GitHub](https://docs.github.com/github/site-policy/github-privacy-statement) y los [Términos de servicio de GitHub](https://docs.github.com/github/site-policy/github-terms-of-service), los [Términos de servicio corporativos de GitHub](https://docs.github.com/github/site-policy/github-corporate-terms-of-service) o los [Términos de producto adicionales](https://docs.github.com/github/site-policy/github-additional-product-terms). Si [Notifica un problema](/visualstudio/ide/how-to-report-a-problem-with-visual-studio), acepta las [Condiciones de uso de Microsoft](https://www.microsoft.com/legal/terms-of-use) y la [Declaración de privacidad de Microsoft](https://privacy.microsoft.com/en-us/privacystatement). Si usa el servicio NuGet, acepta las [Condiciones de uso de NuGet](https://www.nuget.org/policies/Terms) y la [Declaración de privacidad de Microsoft](https://privacy.microsoft.com/en-us/privacystatement). 

Al instalar Visual Studio, [opcionalmente puede seleccionar cargas de trabajo y componentes para instalar](/visualstudio/install/install-visual-studio). Las cargas de trabajo y los componentes pueden aprovechar software de terceros y habilitar experiencias conectadas, en función de su funcionalidad. Por ejemplo, la [descarga de la carga de trabajo Desarrollo de Azure permite publicar las aplicaciones en la nube en Azure](https://visualstudio.microsoft.com/vs/features/azure/). En función de las selecciones de instalación, también puede usar el menú Herramientas y opciones para conectarse, configurar y utilizar experiencias conectadas. Por ejemplo, puede conectarse a un servidor, agregar autenticación de Servicios de Azure o cambiar la configuración de IntelliCode o LiveShare.  

También puede usar la [configuración de firewall](/visualstudio/install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server) de la organización para habilitar o deshabilitar la conexión a los servicios. Tenga en cuenta que deshabilitar la conexión a un punto de conexión puede afectar negativamente o deshabilitar el rendimiento de las características de Visual Studio relacionadas. 

Por último, Visual Studio Marketplace ofrece extensiones que pueden habilitar experiencias conectadas propias o de terceros. Visual Studio Marketplace está sujeto a las [Condiciones de uso de Visual Studio Marketplace](https://cdn.vsassets.io/v/M146_20190123.39/_content/Microsoft-Visual-Studio-Marketplace-Terms-of-Use.pdf) y a la [Declaración de privacidad de Microsoft](https://privacy.microsoft.com/en-us/privacystatement). Cada extensión necesita un contrato con determinados términos de uso y declaración de privacidad asociados a esa oferta.  


## <a name="required-service-data"></a>Datos de servicio necesarios ##

Los datos de servicio necesarios pueden incluir información relacionada con el funcionamiento de la experiencia conectada necesaria para mantener el servicio subyacente protegido, actualizado y funcionando según lo previsto. Si decide usar una experiencia conectada que analice el contenido, por ejemplo IntelliCode, el código que seleccione para el modelo también se enviará y procesará para proporcionarle la experiencia conectada. Los datos de servicio necesarios también pueden incluir la información necesaria para que una experiencia conectada realice su tarea, como la actualización de un paquete NuGet. Puede administrar los datos de servicio necesarios si elige si quiere usar un servicio determinado declaración de privacidad. Si no usa un servicio, no se recopilan los datos de servicio necesarios. 

Los datos de servicio necesarios son diferentes de los datos de diagnóstico porque los datos de diagnóstico se relacionan con el software que se ejecuta en el dispositivo. La elección de participar en el [Programa para la mejora de la experiencia del usuario de Visual Studio (VSCEIP) controla la configuración de privacidad de los datos de diagnóstico](/visualstudio/ide/visual-studio-experience-improvement-program), pero esta configuración no afecta a si se envían los datos de servicio necesarios. 

## <a name="diagnostic-data-collection"></a>Recopilación de datos de diagnóstico ##

Los datos de diagnóstico se usan para mantener Visual Studio protegido y actualizado, para detectar, diagnosticar y corregir problemas, y también para realizar mejoras en el producto. Los datos de diagnóstico se recopilan y envían a Microsoft sobre software cliente de Visual Studio que se ejecuta en el dispositivo del usuario.

Cuando se deja de participar, no se puede optar a la recopilación de datos de diagnóstico opcional. Para que Visual Studio sea seguro, esté actualizado y funcione según lo esperado, es necesario recopilar algunos datos de diagnóstico. La recopilación de datos de diagnóstico necesaria no se verá afectada por la decisión de no participar en [VSCEIP](/visualstudio/ide/visual-studio-experience-improvement-program). 
