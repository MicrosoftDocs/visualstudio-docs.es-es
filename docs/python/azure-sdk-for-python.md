---
title: SDK de Azure para Python
description: Azure SDK para Python facilita el consumo de servicios de Microsoft Azure en aplicaciones que se ejecutan en cualquier plataforma.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: db391b30305e3fad8384dcbeea611379f0061054
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854222"
---
# <a name="consume-azure-services-using-the-azure-sdk-for-python"></a>Consumo de servicios de Azure mediante el SDK de Azure para Python

Azure SDK para Python facilita el uso y la administración de los servicios de Microsoft Azure en aplicaciones que se ejecutan en Windows, MacOS y Linux.

## <a name="installation"></a>Instalación

Azure SDK se instala desde [Python Package Index](https://pypi.python.org/pypi/azure) (Índice de paquetes de Python).

Instale la **versión estable más reciente** (compatible con Python 2.7 y 3.x) de la siguiente forma:

```command
pip install azure
```

También puede seguir [Instalación de Python y el SDK](https://docs.microsoft.com/azure/python-how-to-install/) en la documentación de Azure.

## <a name="documentation"></a>Documentación

El [Centro para desarrolladores de Azure SDK para Python](https://docs.microsoft.com/python/azure/?view=azure-python) también tiene varios recursos útiles, lo que incluye una serie de tutoriales como:

- [Creación de aplicaciones web en Azure App Service en Linux](/azure/app-service/containers/quickstart-python).
- [Blob storage](/azure/storage/blobs/storage-quickstart-blobs-python)
- [Table storage](/azure/cosmos-db/table-storage-how-to-use-python)
- [Queue storage](/azure/storage/storage-python-how-to-use-queue-storage)
- [Azure Cosmos DB](/azure/cosmos-db/sql-api-python-application)
- [Colas de Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Temas y suscripciones de Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Administración de servicios](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Para las API públicas sin documentación, las pruebas unitarias del [repositorio de GitHub del SDK](https://github.com/Azure/azure-sdk-for-python) son una buena fuente de información:

- [Pruebas unitarias de almacenamiento](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Pruebas unitarias de Service Bus](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Pruebas unitarias de Service Management](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)

## <a name="support"></a>Compatibilidad

El repositorio de GitHub del SDK se encuentra en [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

[Registre los problemas en el repositorio](https://github.com/Azure/azure-sdk-for-python/issues) si encuentra algún problema o tiene preguntas sobre el uso del SDK.
