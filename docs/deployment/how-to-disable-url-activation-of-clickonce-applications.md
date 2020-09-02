---
title: Cómo deshabilitar la activación de direcciones URL de aplicaciones ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3de5272bdb47e0d7d87bad63d5ea0cd6a8b9bef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382463"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Cómo: Deshabilitar la activación de direcciones URL de aplicaciones ClickOnce

Normalmente, una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se inicia automáticamente después de que se instale desde un servidor web. Por motivos de seguridad, puede deshabilitar este comportamiento e indicar a los usuarios que, en su lugar, inicien la aplicación desde el menú **Inicio**. En el procedimiento siguiente, se describe cómo deshabilitar la activación de URL.

Esta técnica se puede utilizar solo para las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instaladas en el equipo del usuario desde un servidor web. No se puede utilizar para aplicaciones solo en línea, que se pueden iniciar utilizando su dirección URL. Para obtener más información acerca de la diferencia entre las aplicaciones solo en línea e instaladas, consulte [Elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

Este procedimiento usa la herramienta del kit de desarrollo de software (SDK) de Windows MageUI.exe. Para obtener más información sobre esta herramienta, consulte [MageUI.exe (Herramienta de generación y edición de manifiestos, cliente gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). También puede realizar este procedimiento con Visual Studio.

## <a name="procedure"></a>Procedimiento

### <a name="to-disable-url-activation-for-your-application"></a>Deshabilitar la activación de direcciones URL para la aplicación

1. Abra el manifiesto de implementación en MageUI.exe. Si aún no ha creado uno, siga los pasos de [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

2. Seleccione la pestaña **Opciones de implementación**.

3. Desactive la casilla de verificación **Ejecutar automáticamente la aplicación después de instalarla**.

4. Guarde y firme el manifiesto.

## <a name="see-also"></a>Consulte también

- [Publicación de aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)