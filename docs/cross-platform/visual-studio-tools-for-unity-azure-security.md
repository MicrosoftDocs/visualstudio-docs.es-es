---
title: Tutorial de seguridad de Visual Studio Tools para Unity Azure| Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: F4FD6E1C-EA64-4613-BDDE-6E4E5CCF983E
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: d036d180fddcce443debe3d7917415380187994c
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="update-unity-mono-security-certificate-store"></a>Actualización del almacén de certificados de seguridad de Unity Mono

Unity Mono se suministra con un almacén de certificados vacío y, por tanto, no confía en cualquier sitio. Puede leer más sobre esto en la página [Mono security FAQ](http://www.mono-project.com/docs/faq/security/) (Preguntas más frecuentes sobre seguridad de Mono).

Para conectarse a Azure sin omitir TLS/SSL, el almacén de certificados de Mono Unity debe estar actualizado.

## <a name="using-mozroots-to-install-certificates"></a>Usar mozroots para instalar certificados

La herramienta mozroots se incluye en Mono. Descarga e instala la lista de certificados raíz de Mozilla.

1. Abra el terminal del símbolo del sistema.

2. Navegue por el terminal al directorio **C:\Archivos de programa\Unity\Editor\Data\MonoBleedingEdge\bin >**. La ubicación exacta puede variar según dónde esté instalado Unity en el equipo local.

3. Escriba el siguiente comando y presione **Entrar** para ejecutarlo:

  `mono ..\lib\mono\4.5\mozroots.exe --sync --import`

4. Obtendrá el siguiente resultado (aunque el número o los certificados agregados pueden variar):

  ```
  Downloading from 'https://hg.mozilla.org/releases/mozilla-release/raw-file/default/security/nss/lib/ckfw/builtins/certdata.txt'...
  Importing certificates into user store...
  1 new root certificates were added to your trust store.
  Import process completed.
  ```

5. Ahora debería poder ejecutar el proyecto de ejemplo sin recibir errores relacionados de TLS.

## <a name="next-step"></a>Paso siguiente

* [Probar la conexión de cliente](visual-studio-tools-for-unity-azure-connection.md)
