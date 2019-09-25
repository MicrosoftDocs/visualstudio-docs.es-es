---
title: 'CA5350: No usar algoritmos criptográficos no seguros'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4aecd052e86a4c0366a1a43cb985ad50ab8862d8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236957"
---
# <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: No usar algoritmos criptográficos no seguros

|||
|-|-|
|TypeName|DoNotUseWeakCryptographicAlgorithms|
|Identificador de comprobación|CA5350|
|Categoría|Microsoft.Cryptography|
|Cambio importante|Poco problemático|

> [!NOTE]
> Esta advertencia se actualizó por última vez en noviembre de 2015.

## <a name="cause"></a>Motivo

Los algoritmos de cifrado como <xref:System.Security.Cryptography.TripleDES> y los algoritmos hash como <xref:System.Security.Cryptography.SHA1> y <xref:System.Security.Cryptography.RIPEMD160> se consideran no seguros.

Estos algoritmos criptográficos no proporcionan tantas garantías de seguridad como sus equivalentes más modernos. Los algoritmos hash criptográfico <xref:System.Security.Cryptography.SHA1> y <xref:System.Security.Cryptography.RIPEMD160> proporcionan menos resistencia a colisiones que los algoritmos hash más modernos. El algoritmo de cifrado <xref:System.Security.Cryptography.TripleDES> proporciona menos bits de seguridad que los algoritmos de cifrado más modernos.

## <a name="rule-description"></a>Descripción de la regla

Las funciones hash y los algoritmos de cifrado no seguros se usan hoy en día por varios motivos, pero no deben usarse para garantizar la confidencialidad o la integridad de los datos que protegen.

La regla se desencadena cuando encuentra los algoritmos 3DES, SHA1 o RIPEMD160 en el código y lanza una advertencia al usuario.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Use opciones de criptografía más segura:

- Para el cifrado TripleDES, use el cifrado <xref:System.Security.Cryptography.Aes> .

- Para las funciones hash SHA1 o RIPEMD160, use los de la familia [SHA-2](/windows/desktop/SecCrypto/hash-and-signature-algorithms) (por ejemplo, <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>y <xref:System.Security.Cryptography.SHA256>).

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Suprima una advertencia de esta regla cuando el nivel de protección necesario para los datos no requiera una garantía de seguridad.

## <a name="pseudo-code-examples"></a>Ejemplos de pseudocódigo

En el momento de redactar este artículo, el ejemplo de pseudocódigo siguiente muestra el patrón que esta regla detecta.

### <a name="sha-1-hashing-violation"></a>Infracción de hash SHA-1

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA1.Create();
```

Solución:

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="ripemd160-hashing-violation"></a>Infracción de hash RIPEMD160

```csharp
using System.Security.Cryptography;
...
var hashAlg = RIPEMD160Managed.Create();
```

Solución:

```csharp
using System.Security.Cryptography;
...
var hashAlg = SHA256.Create();
```

### <a name="tripledes-encryption-violation"></a>Infracción de cifrado TripleDES

```csharp
using System.Security.Cryptography;
...
using (TripleDES encAlg = TripleDES.Create())
{
  ...
}
```

Solución:

```csharp
using System.Security.Cryptography;
...
using (AesManaged encAlg = new AesManaged())
{
  ...
}
```