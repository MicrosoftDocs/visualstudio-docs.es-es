---
title: Acceso a nubes privadas de Azure con Visual Studio | Microsoft Docs
description: Obtenga información sobre cómo obtener acceso a recursos de nube privada mediante Visual Studio.
author: ghogen
manager: douge
assetId: 9d733c8d-703b-44e7-a210-bb75874c45c8
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/13/2017
ms.author: ghogen
ms.openlocfilehash: 216b85e0ebf42b79c388ce217d548f2dce3c86b6
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002965"
---
# <a name="accessing-private-azure-clouds-with-visual-studio"></a>Acceso a nubes privadas de Azure con Visual Studio

De forma predeterminada, Visual Studio admite extremos REST de nube de Azure. En este artículo, aprenderá a usar el certificado de la nube privada para acceder e interactuar con la nube privada desde Visual Studio.

1. En el portal de Azure para la nube privada, descargue el archivo de configuración de publicación o póngase en contacto con su administrador para un archivo de configuración de publicación. (El archivo tiene la extensión `.publishsettings`.)

1. En Visual Studio **Explorador de servidores**, haga clic en el **Azure** nodo y seleccione **administrar y filtrar suscripciones**.

    ![Comando Administrar suscripciones](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790778.png)

1. En el **administrar suscripciones de Microsoft Azure** cuadro de diálogo, seleccione el **certificados** y, después, seleccione **importación**.

    ![Importación de certificados de Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790779.png)

1. En el **Importar suscripciones de Microsoft Azure** cuadro de diálogo, seleccione **examinar**.

    ![Busque el botón en el cuadro de diálogo Importar suscripciones de Microsoft Azure](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/browse-button.png)

1. En el **abierto** cuadro de diálogo, vaya al directorio donde guardó el archivo de configuración de publicación, seleccione el archivo y, a continuación, seleccione **abierto**.

    ![Seleccione el archivo de configuración de publicación](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/select-publish-settings-file.png)

1. Cuando se devuelve a la **Importar suscripciones de Microsoft Azure** cuadro de diálogo, seleccione **importación**.

    ![Importe el archivo de configuración de publicación](./media/vs-azure-tools-access-private-azure-clouds-with-visual-studio/IC790780.png)

    Los certificados se importan desde el archivo de configuración de publicación en Visual Studio, y ahora puede interactuar con los recursos de nube privada.

