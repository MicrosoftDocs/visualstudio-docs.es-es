---
title: "Guía del administrador de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 04/06/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 47c39bd711b69efdb863d71f11e3e472054a3ce3
ms.openlocfilehash: aebd3abc671f997773fc7c557627ca23b9bf82bd
ms.lasthandoff: 04/06/2017

---
# <a name="visual-studio-administrator-guide-for-visual-studio-2017"></a>Guía del administrador de Visual Studio para Visual Studio 2017

 Puede implementar Visual Studio en una red siempre y cuando cada equipo de destino cumpla los [requisitos mínimos de instalación](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs).

 Tanto si va a realizar la implementación a través de software como System Center o mediante un archivo por lotes, normalmente deberá seguir los pasos siguientes:

1. [Almacenar en caché el diseño del producto de Visual Studio](create-an-offline-installation-of-visual-studio.md) en una ubicación de red.

2. [Seleccionar las cargas de trabajo y los componentes](workload-and-component-ids.md) que quiere instalar.

3. [Compilar un script de instalación](use-command-line-parameters-to-install-visual-studio.md) mediante los elementos seleccionados y otros parámetros de la línea de comandos para controlar la instalación.

4. Opcionalmente, [aplicar una clave de producto de licencia por volumen](automatically-apply-product-keys-when-deploying-visual-studio.md) como parte del script de instalación para que los usuarios no tengan que activar el software por separado.

5. Usar la tecnología de implementación de su elección para ejecutar el script generado en los pasos anteriores en las estaciones de trabajo de destino de los desarrolladores.

6. Actualizar la ubicación de red con las actualizaciones más recientes para Visual Studio mediante la ejecución del comando usado en el paso 1 de forma periódica para agregar componentes actualizados.

> [!IMPORTANT]
>  Tenga en cuenta que las instalaciones que se realizan desde un recurso compartido de red "recordarán" la ubicación de la que proceden. Esto significa que, para reparar un equipo cliente, quizás sea necesario volver al recurso compartido de red desde el que se instaló el cliente. Elija cuidadosamente la ubicación de red para que esté disponible durante el tiempo que espera que los clientes de Visual Studio 2017 se ejecuten en su organización.

## <a name="tools"></a>Herramientas

 Dispone de varias herramientas que le ayudarán a detectar y administrar las instancias de Visual Studio instaladas en los equipos cliente:

* [VSWhere](https://github.com/microsoft/vswhere): ejecutable de C++ que ayuda a encontrar la ubicación de las herramientas principales de Visual Studio desde una instancia instalada de Visual Studio.
* [VSSetup.PowerShell](https://github.com/microsoft/vssetup.powershell): scripts de PowerShell que usan la API de configuración de la instalación para identificar las instancias instaladas de Visual Studio.
* [VS-Setup-Samples](https://github.com/microsoft/vs-setup-samples): ejemplos de C# y C++ que muestran cómo usar la API de configuración de la instalación para consultar una instalación existente.

Además, la [API de configuración de la instalación](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.setup.configuration.aspx) proporciona interfaces para los desarrolladores que quieran crear sus propias utilidades para interrogar instancias de Visual Studio.

>[!TIP]
>Para más información sobre la instalación de Visual Studio 2017, vea los [artículos del blog de Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/).


## <a name="see-also"></a>Vea también
* [Instalación de Visual Studio 2017](install-visual-studio.md)
* [Creación de un instalador sin conexión para Visual Studio 2017](create-an-offline-installation-of-visual-studio.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [Ejemplos de parámetros de línea de comandos](command-line-parameter-examples.md)
* [Notificar un problema con Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

