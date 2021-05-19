---
title: Uso de la identidad administrada con Bridge to Kubernetes
ms.technology: vs-azure
ms.date: 04/28/2021
ms.topic: conceptual
description: Aprenda a usar una identidad administrada de Azure Active Directory (Azure AD) en un clúster de AKS con Bridge to Kubernetes.
monikerRange: '>=vs-2019'
manager: jmartens
author: ghogen
ms.author: ghogen
ms.openlocfilehash: e4847b25531b48c8200a2620ca3e975f9677c881
ms.sourcegitcommit: 60b7a6159045a44293043a519c8ea6d915bf2c31
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/01/2021
ms.locfileid: "108335106"
---
# <a name="use-managed-identity-with-bridge-to-kubernetes"></a>Uso de la identidad administrada con Bridge to Kubernetes

Si el clúster de AKS usa características de seguridad de [identidad administrada](/azure/active-directory/managed-identities-azure-resources/overview) para proteger el acceso a secretos y recursos, Bridge to Kubernetes necesita una configuración especial para asegurarse de que puede funcionar con estas características. Es necesario descargar un token de Azure Active Directory (AD) en el equipo local para asegurarse de que la ejecución y depuración locales están correctamente protegidas, lo que requiere una configuración especial en Bridge to Kubernetes. En este artículo se muestra cómo configurar Bridge to Kubernetes para que funcione con servicios que usan identidad administrada.

## <a name="how-to-configure-your-service-to-use-managed-identity"></a>Configuración del servicio para usar la identidad administrada

Para habilitar una máquina local compatible con la identidad administrada, en el archivo *KubernetesLocalConfig.yaml*, en la sección `enableFeatures`, agregue `ManagedIdentity`. Agregue la sección `enableFeatures` si aún no está ahí.

```yaml
enableFeatures:
    ManagedIdentity
```

> [!WARNING]
> Asegúrese de usar solo la identidad administrada para Bridge to Kubernetes al trabajar con clústeres de desarrollo, no con clústeres de producción, porque el token de Azure AD se captura en la máquina local, lo que presenta un riesgo de seguridad potencial.

Si no tiene un archivo *KubernetesLocalConfig.yaml*, puede crear uno; vea [Configuración de Bridge to Kubernetes](configure-bridge-to-kubernetes.md).

## <a name="how-to-fetch-the-azure-active-directory-tokens"></a>Captura de los tokens de Azure Active Directory

Debe asegurarse de que se basa en <xref:Azure.Identity.DefaultAzureCredential> o <xref:Azure.Identity.ManagedIdentityCredential> en el código cuando captura el token.

El siguiente código de C# muestra cómo capturar las credenciales de la cuenta de almacenamiento cuando se usa `ManagedIdentityCredential`:

```csharp
var credential = new ManagedIdentityCredential(miClientId);
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

El siguiente código muestra cómo capturar las credenciales de la cuenta de almacenamiento cuando se usa DefaultAzureCredential:

```csharp
var credential = new DefaultAzureCredential();
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

Para obtener información sobre cómo acceder a otros recursos de Azure mediante la identidad administrada, consulte la sección [Pasos siguientes](#next-steps).

## <a name="receive-azure-alerts-when-tokens-are-downloaded"></a>Recepción de alertas de Azure cuando se descargan tokens

Cada vez que usa Bridge to Kubernetes en un servicio, el token de Azure AD se descarga en el equipo local. Puede habilitar alertas de Azure para recibir notificaciones cuando esto ocurra. Para más información, consulte [Habilitación de Azure Defender](/azure/security-center/enable-azure-defender). Tenga en cuenta que hay un cargo (después de un período de prueba de 30 días).

## <a name="next-steps"></a>Pasos siguientes

Ahora que ha configurado Bridge to Kubernetes para que funcione con el clúster de AKS que usa la identidad administrada, puede depurar de la forma habitual. Consulte [bridge-to-kubernetes.md#connect-to-your-cluster-and-debug-a-service].

Para más información sobre el uso de la identidad administrada para acceder a los recursos de Azure, consulte estos tutoriales:

- [Tutorial: Uso de identidades administradas asignadas por el sistema de una máquina virtual Linux para acceder a Azure Storage](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-storage)
- [Tutorial: Uso de identidades administradas asignadas por el sistema de una máquina virtual Linux para acceder a Azure Data Lake Store](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-datalake)
- [Tutorial: Uso de identidades administradas asignadas por el sistema de una máquina virtual Linux para acceder a Azure Key Vault](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-nonaad)

También hay otros tutoriales en esa sección para usar la identidad administrada para acceder a otros recursos de Azure.

## <a name="see-also"></a>Consulte también

[Azure Active Directory](/azure/active-directory/managed-identities-azure-resources/)
