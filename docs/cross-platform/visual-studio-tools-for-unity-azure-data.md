---
title: 'Tutorial de Azure para Visual Studio Tools para Unity: modelo de datos| Microsoft Docs'
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6FCCA8D1-0D06-4B2A-A55F-FC3D1FEA0F56
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: e3b6064a3947f57ffcbe6422162c6c72fca0ab21
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="create-data-model-classes"></a>Crear clases de modelo de datos

El proyecto de Unity debe contener clases de modelo de datos que se correspondan con las tablas creadas en el back-end de la aplicación móvil de Azure.

## <a name="create-the-crashinfo-class"></a>Crear la clase CrashInfo

1. En Unity, agregue una carpeta nueva en el directorio raíz **Recursos** denominada **Scripts**. Dentro de la nueva carpeta Scripts, cree otra carpeta denominada **Modelos de datos**. Este paso es solo a efectos de organización.

2. Dentro de la nueva carpeta Modelos de datos, cree un script de C# denominado **CrashInfo**.

3. Abra el script `CrashInfo`, elimine todo el código de plantilla, incluida la declaración de clase y las instrucciones Using, y agregue lo siguiente:

  ```csharp
  public class CrashInfo
  {
      public string Id { get; set; }
      public float X { get; set; }
      public float Y { get; set; }
      public float Z { get; set; }
  }
  ```

  > [!WARNING]
  > Para que el tutorial funcione correctamente, el nombre de la clase de modelo de datos debe coincidir con el nombre de la tabla fácil creada en el back-end de la aplicación móvil de Azure.

## <a name="create-the-highscoreinfo-class"></a>Crear la clase HighScoreInfo

1. En la carpeta Modelos de datos, cree un script de C# denominado **HighScoreInfo**.

2. Abra el script `HighScoreInfo`, elimine todo el código de plantilla, incluida la declaración de clase y las instrucciones Using, y agregue lo siguiente:

  ```csharp
  public class HighScoreInfo
  {
      public string Name { get; set; }
      public float Time { get; set; }
      public string Id { get; set; }
  }
  ```

  ## <a name="next-step"></a>Paso siguiente

  * [Implementación de MobileServiceClient de Azure](visual-studio-tools-for-unity-azure-mobile-client.md)
