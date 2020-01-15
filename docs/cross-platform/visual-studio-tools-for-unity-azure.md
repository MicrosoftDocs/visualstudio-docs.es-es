---
title: Programación con Visual Studio Tools para Unity | Microsoft Docs
ms.custom: ''
ms.date: 12/18/2017
ms.reviewer: crdun
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 7921D4C7-5526-42F5-8E03-82D3E33A893F
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: e9a07a7f04cae433803d012302555821fc851075
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916824"
---
# <a name="program-with-unity-and-azure"></a>Programa con Unity y Azure

Azure ofrece una solución escalable para almacenar telemetría y otros datos del juego en la nube. Con el lanzamiento de Unity 2017, la compatibilidad experimental de Unity con .NET 4.6 hace que la integración de Azure sea más fácil que nunca, ya que permite el uso de los SDK de .NET de Azure.

## <a name="experimental-azure-sdks"></a>SDK de Azure experimental

> [!NOTE]
> Estos SDK son no compatibles, pero se proporcionan para ayudar a los clientes a probar la compatibilidad experimental de .NET 4.6 con Unity.

Visite [The Sandbox](/sandbox/) para probar los siguientes SDK de Azure experimentales con Unity:

* [Azure Storage SDK for Unity](/sandbox/gamedev/unity/azure-storage-unity?wt.mc_id=azgamedev-sandbox-brpeek) (SDK de Azure Storage para Unity)
* [Azure Storage SDK for Unity](/sandbox/gamedev/unity/azure-event-hubs-unity?WT.mc_id=azgamedev-sandbox-brpeek) (SDK de Event Hubs de Azure para Unity)
* [Azure Mobile Apps SDK for Unity](/sandbox/gamedev/unity/azure-mobile-apps-unity?WT.mc_id=azgamedev-sandbox-brpeek) (SDK de Mobile Apps de Azure para Unity)

## <a name="azure-sdk-sample"></a>Ejemplo de SDK de Azure

También hay un [juego de ejemplo sencillo](/sandbox/gamedev/unity/samples/azure-mobile-apps-unity-racer) en el que se utiliza el SDK de tablas fáciles de Azure y Unity. En este juego se usa el almacenamiento de datos de tablas fáciles de Azure para realizar el seguimiento de la tabla de clasificación de alta puntuación y la telemetría del juego, y está disponible para su [descarga desde GitHub](https://github.com/BrianPeek/AzureSamples-Unity).

![Captura de pantalla de juego de ejemplo](media/vstu_azure-test-sample-game-image2.png)
