---
layout: bidder
title: VIS.X
description: Prebid VIS.X Bidder Adaptor
hide: true
biddercode: visx
gdpr_supported: true
---

### Note
To be able to use the full bandwidth of VIS.X high impact ad products, we strongly recommend disabling SafeFrames:
- If you are using Google Ad Manager (GAM), make sure the “Serve in Safeframe” box in creative settings is unchecked,
- If you are using AppNexus Seller Tag, make sure the enableSafeFrame parameter is set to False.

If you require SafeFrames to be activated, please reach out to your YOC account manager to obtain further details.

The YOC VIS.X adaptor requires setup and approval from your YOC account manager team, even for existing YOC publishers. Please reach out to your account manager to enable Prebid.js for your account.

### Bid params

{: .table .table-bordered .table-striped }
| Name        | Scope    | Description                                                                                                                                                                                                                                 | Example    | Type     |
|-------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|----------|
| `uid`       | required | The publisher's ad unit ID in VIS.X                                                                                                                                                                                                         | `'903536'` | `string` |

### Configuration

The VIS.X adaptor has the ability to work in different currencies. Currently this adaptor supports `'EUR'`, `'USD'`, `'GBP'`, `'PLN'`. Defaults to `'EUR'`.

```javascript
$$PREBID_GLOBAL$$.setConfig({
    currency: {
        adServerCurrency: 'GBP'
    }
});
```
Note: this currency config should correspond with your VIS.X account setting. Please reach out to your account manager for more information.
