---
title: Tutorial de Visual Studio Tools para Unity Azure| Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7921D4C7-5526-42F5-8E03-82D3E33A893F
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: d5242dd873591abee15f528d09b6f588ea12f5ba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="using-azure-easy-tables-with-unity-walkthrough"></a>Tutorial del uso de tablas fáciles de Azure con Unity

![Captura de pantalla de juego de ejemplo](media/vstu_azure-test-sample-game-image2.png)

## <a name="introduction"></a>Introducción

Azure ofrece una solución escalable para almacenar telemetría y otros datos del juego en la nube. Con el lanzamiento de Unity 2017, la compatibilidad de Unity con .NET 4.6 hace que la integración de Azure sea más fácil que nunca, ya que permite el uso del SDK de Azure Mobile Client.

Estos pasos le guiarán a través del proceso de configuración de un proyecto de Unity que aproveche Azure para guardar los datos de telemetría y de la tabla de clasificación en la nube.

> [!NOTE]
> Este proyecto requiere el tiempo de ejecución de scripting "experimental" de Mono de .NET 4.6 en Unity 2017. [Unity ha declarado que pronto este será el valor predeterminado](https://forum.unity3d.com/threads/future-plans-for-the-mono-runtime-upgrade.464327/), pero por ahora sigue considerándose experimental y podría surgir algún problema.

> En este tutorial se muestra un ejemplo para conectarse a un back-end de Azure Mobile App desde una compilación para equipo de Unity. En el momento de elaboración de este documento, existen problemas conocidos que impiden que este proyecto funcione en las plataformas Mac y Android. Aunque se sabe que estos problemas conocidos se corregirán, no es seguro cuándo sucederá. Para obtener más información, visite el [foro de scripting experimental](https://forum.unity3d.com/forums/experimental-scripting-previews.107/) de Unity.

## <a name="download-the-completed-project"></a>Descargar el proyecto completado

El proyecto completado está disponible en GitHub. A pesar de ello, en el tutorial se da por supuesto que se parte de un proyecto nuevo vacío y se proporcionan vínculos para descargar recursos cuando sea necesario.

## <a name="walkthrough-steps"></a>Pasos del tutorial

1. [Configuración de tablas sencillas en Azure](visual-studio-tools-for-unity-azure-configure.md)
2. [Creación de tablas sencillas](visual-studio-tools-for-unity-azure-setup.md)
3. [Preparación del entorno de desarrollo](visual-studio-tools-for-unity-azure-prepare.md)
4. [Creación de clases de modelo de datos](visual-studio-tools-for-unity-azure-data.md)
5. [Implementación de MobileServiceClient de Azure](visual-studio-tools-for-unity-azure-mobile-client.md)
6. [Actualización del almacén de certificados de seguridad de Unity Mono](visual-studio-tools-for-unity-azure-security.md)
7. [Prueba de la conexión de cliente](visual-studio-tools-for-unity-azure-connection.md)
7. [Importación de los recursos de juego de muestra](visual-studio-tools-for-unity-azure-game-assets.md)
8. [Prueba de juegos de muestra](visual-studio-tools-for-unity-azure-game.md)
9. [Explicación de RaceScene](visual-studio-tools-for-unity-azure-racescene.md)
10. [Explicación de HeatmapScene](visual-studio-tools-for-unity-azure-heatmapscene.md)
11. [Explicación de LeaderboardScene](visual-studio-tools-for-unity-azure-leaderboardscene.md)


## <a name="next-step"></a>Paso siguiente
* [Configuración de tablas sencillas en Azure](visual-studio-tools-for-unity-azure-configure.md)
