---
title: Azure SDK para Python | Microsoft Docs
description: Azure SDK para Python facilita el consumo de servicios de Microsoft Azure en aplicaciones que se ejecutan en cualquier plataforma.
ms.custom: ''
ms.date: 01/22/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 3f03ca08dddb90f6eb86a439f7f92307df3b4335
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2018
---
# <a name="azure-sdk-for-python"></a>SDK de Azure para Python

Azure SDK para Python facilita el uso y la administración de los servicios de Microsoft Azure en aplicaciones que se ejecutan en Windows, Mac OS X y Linux.

## <a name="installation"></a>Instalación

Azure SDK se instala desde [Python Package Index](https://pypi.python.org/pypi/azure) (Índice de paquetes de Python).

Instale la **versión estable más reciente** (compatible con Python 2.7 y 3.x) de la siguiente forma:

```command
pip install azure
```

También puede seguir [Instalación de Python y el SDK](https://docs.microsoft.com/azure/python-how-to-install/) en la documentación de Azure.

## <a name="documentation"></a>Documentación

Puede encontrar documentación en [azure-sdk-for-python.readthedocs.org](http://azure-sdk-for-python.readthedocs.org/en/latest/index.html).

El [Centro para desarrolladores de Azure SDK para Python](http://azure.microsoft.com/develop/python/) también tiene varios recursos útiles, lo que incluye una serie de tutoriales como:

- Creación de aplicaciones web con [Django](/azure/app-service-web/web-sites-python-create-deploy-django-app), [Flask](/azure/app-service-web/web-sites-python-create-deploy-flask-app) y [Bottle](/azure/app-service-web/web-sites-python-create-deploy-bottle-app).
- [Blob storage](/azure/storage/storage-python-how-to-use-blob-storage)
- [Table storage](/azure/storage/storage-python-how-to-use-table-storage)
- [Queue storage](/azure/storage/storage-python-how-to-use-queue-storage)
- [Azure Cosmos DB](/azure/cosmos-db/sql-api-python-application)
- [Colas de Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Temas y suscripciones de Service Bus](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Administración de servicios](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Para las API públicas sin documentación, las pruebas unitarias del [repositorio de GitHub del SDK](https://github.com/Azure/azure-sdk-for-python) son una buena fuente de información:

- [Pruebas unitarias de almacenamiento](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Pruebas unitarias de Service Bus](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Pruebas unitarias de Service Management](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)
- [Pruebas unitarias de Administración de recursos](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)

## <a name="support"></a>Compatibilidad

El repositorio de Git del SDK se encuentra en [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

[Registre los problemas en el repositorio](https://github.com/Azure/azure-sdk-for-python/issues) si encuentra algún problema o tiene preguntas sobre el uso del SDK.
