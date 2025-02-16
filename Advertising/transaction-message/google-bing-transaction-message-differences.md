---
title: "Differences Between Google&#39;s and Bing&#39;s Transaction Message Usage"
description: Lists the difference in usage between Bing's and Google's transaction message.
ms.service: "hotel-ads-transaction-message"
ms.topic: "article"
author: "swhite-msft"
manager: ehansen
ms.author: "scottwhi"
---

# Differences between Google's and Bing's Transaction Message

The following are the differences between Google's Transaction Message implementation and Bing's.

- Bing does not support (and will ignore) the following [Transaction](reference.md#transactiontype) elements:  
  
  - `PartnerData`
  
- Bing does not support (and will ignore) the following [Transaction](reference.md#transaction) attributes:  
  
  - `id`
  - `partner`
  
- Bing does not support (and will ignore) the following [Result](reference.md#resulttype) elements:
  
  - `Rates`
  
- Bing does not support (and will ignore) the `all_inclusive` attribute of the `Baserate` element (see [Result](reference.md#resulttype)).
