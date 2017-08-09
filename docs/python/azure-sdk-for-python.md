---
title: Azure SDK para Python | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d30fddae-8e2f-4f50-90d3-8ed2cd35c7a6
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: c64d1abc2266b7e2edbb2c81a46c53c39eb9a85a
ms.contentlocale: es-es
ms.lasthandoff: 07/18/2017

---

# <a name="azure-sdk-for-python"></a>SDK de Azure para Python

Azure SDK para Python facilita el uso y la administración de los servicios de Microsoft Azure en aplicaciones que se ejecutan en Windows, Mac OS X y Linux.

## <a name="installation"></a>Instalación

Azure SDK se instala desde [Python Package Index](https://pypi.python.org/pypi/azure) (Índice de paquetes de Python).

Instale la **versión estable más reciente** (compatible con Python 2.7 y 3.3 +) como sigue:

```bash
pip install azure
```

También puede seguir [Instalación de Python y el SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/) en la documentación de Azure.

## <a name="documentation"></a>Documentación

Puede encontrar documentación en [azure-sdk-for-python.readthedocs.org](http://azure-sdk-for-python.readthedocs.org/en/latest/index.html).

El [Centro para desarrolladores de Azure SDK para Python](http://azure.microsoft.com/develop/python/) también tiene varios recursos útiles, incluida una serie de tutoriales como:

  - Creación de aplicaciones web con [Django](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions), [Flask](https://docs.microsoft.com/azure/app-service-web/web-sites-python-create-deploy-flask-app) y [Bottle](https://docs.microsoft.com/azure/app-service-web/web-sites-python-create-deploy-bottle-app).
  - [Blob storage](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-blob-storage)
  - [Table storage](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-table-storage)
  - [Queue storage](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-queue-storage)
  - [DocumentDB](https://docs.microsoft.com/azure/documentdb/documentdb-python-application)
  - [Colas de Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
  - [Temas y suscripciones de Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
  - [Administración de servicios](https://docs.microsoft.com/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Para las API públicas sin documentación, las pruebas unitarias del [repositorio de GitHub del SDK](https://github.com/Azure/azure-sdk-for-python) son una buena fuente de información:

- [Pruebas unitarias de almacenamiento](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Pruebas unitarias de Service Bus](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Pruebas unitarias de Service Management](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)
- [Pruebas unitarias de Administración de recursos](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)

## <a name="support"></a>Compatibilidad

El repositorio de GIT para el SDK se encuentra en [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

[Registre los problemas en el repositorio](https://github.com/Azure/azure-sdk-for-python/issues) si encuentra algún problema o tiene preguntas sobre el uso del SDK.
