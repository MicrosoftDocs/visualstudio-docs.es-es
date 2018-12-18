---
title: 'Cómo: deshabilitar la activación de direcciones URL de aplicaciones ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ab9204513c59d2c853c0a3738ef2363739d56c1
ms.sourcegitcommit: 551f13774e8bb0eb47cbd973745628a956e866aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2018
ms.locfileid: "49459626"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Cómo: deshabilitar la activación de direcciones URL de aplicaciones ClickOnce

Normalmente, una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] se inicia automáticamente después de que se instale desde un servidor web. Por motivos de seguridad, puede decidir deshabilitar este comportamiento e indicar a los usuarios para iniciar la aplicación desde el **iniciar** menú en su lugar. En el procedimiento siguiente, se describe cómo deshabilitar la activación de URL.

Esta técnica se puede utilizar solo para las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instaladas en el equipo del usuario desde un servidor web. No se puede utilizar para aplicaciones solo en línea, que se pueden iniciar utilizando su dirección URL. Para obtener más información sobre la diferencia entre las aplicaciones sólo en línea e instaladas, consulte [elegir una estrategia de implementación de ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

Este procedimiento usa la herramienta de Kit de desarrollo de Software (SDK) de Windows MageUI.exe. Para obtener más información sobre esta herramienta, consulte [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). También puede realizar este procedimiento con Visual Studio.

## <a name="procedure"></a>Procedimiento

### <a name="to-disable-url-activation-for-your-application"></a>Deshabilitar la activación de direcciones URL para la aplicación

1.  Abra el manifiesto de implementación en MageUI.exe. Si aún no ha creado uno, siga los pasos descritos en [Tutorial: implementar manualmente una aplicación ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

2.  Seleccione el **opciones de implementación** ficha.

3.  Desactive el **ejecutar automáticamente la aplicación después de instalar** casilla de verificación.

4.  Guarde y firme el manifiesto.

## <a name="see-also"></a>Vea también

- [Publicar aplicaciones ClickOnce](../deployment/publishing-clickonce-applications.md)