---
title: How to work With GST/HST on Sales and Purchases
description: 'This topic describes the various ways of working with GST/HST both manually and with automatic setup, to help you meet country specific regulations.'
author: brentholtorf
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 'VAT, sales, purchases'
ms.search.form: '7, 118, 130, 142, 459, 460, 525'
ms.date: 06/16/2021
ms.author: bholtorf
---
# <a name="work-with-vat-on-sales-and-purchases" />Work with GST/HST on Sales and Purchases

If your country or region requires you to calculate and report value-added tax (VAT) on sales and purchase transactions, you can set up [!INCLUDE[prod_short](includes/prod_short.md)] to calculate VAT. For more information, see [Setting Up to Calculations and Posting Methods for GST/HST](finance-setup-vat.md).

There are, however, some GST/HST-related tasks that you can do manually. For example, you might need to correct a posted amount if you discover that a vendor uses a different rounding method.  

> [!TIP]
> You can let [!INCLUDE[prod_short](includes/prod_short.md)] validate GST/HST identification numbers and other company information when you create or update documents. For more information, see [Validate GST/HST Identification Numbers](finance-how-validate-vat-registration-number.md).

## <a name="calculating-and-displaying-vat-amounts-on-sales-and-purchase-documents" />Calculating and displaying GST/HST amounts on sales and purchase documents

When you choose an item number in the **No.** field on a sales or purchase document, [!INCLUDE[prod_short](includes/prod_short.md)] fills in the **Unit Price** and **Line Amount** fields. The unit price comes from either the **Item** card or the item prices allowed for the item and customer. [!INCLUDE[prod_short](includes/prod_short.md)] calculates the line amount when you enter a quantity for the line.  

If you want the unit prices and line amounts to include GST/HST, for example, if you are selling to retail consumers, choose the **Prices Including GST/HST** check box on the document. For more information, see [Including or Excluding GST/HST in Prices and Line Amounts](#including-or-excluding-vat-in-prices-and-line-amounts). 

You can calculate and display GST/HST amounts in sales and purchase documents differently, depending on the type of customer or vendor you're dealing with. You can also change the calculated GST/HST amount manually, for example, so that it matches the GST/HST amount calculated by your vendor on a given transaction.

### <a name="including-or-excluding-vat-in-prices-and-line-amounts" />Including or excluding GST/HST in prices and line amounts

If you choose the **Prices Including GST/HST** checkbox on a sales document, the **Unit Price** and **Line Amount** fields will include GST/HST. By default, the values in these fields do not include GST/HST. The names of the fields reflect whether prices include GST/HST.  

You can set up the default setting of the **Prices Including GST/HST** for all sales documents for a customer in the **Prices Including GST/HST** field on the **Customer** card. You can also set up item prices to include or exclude GST/HST. Typically, prices on the Item Card will exclude GST/HST. 

The following table provides an overview of how application calculates the unit price amounts for a sales document when you have not set up prices on the **Sales Prices** page:  

|**Price Includes GST/HST field on Item Card**|**Prices Including GST/HST field**|**Action Performed**|  
|-----------------------------------------------|----------------------------------------------------|--------------------------|  
|Not Enabled|Not Enabled|The **Unit Price** on the Item Card is copied to **Unit Price Excl. GST/HST** field on the sales lines.|  
|Not Enabled|Enabled|The application calculates the GST/HST amount per unit and adds to the **Unit Price** on the Item Card. This total unit price is then entered in the **Unit Price Incl. GST/HST field** on the sales lines.|  
|Enabled|Not Enabled|The application calculates the GST/HST amount included in the **Unit Price** field on the **Item Card** using the GST/HST percentage related to the GST/HST Bus. Posting Gr. (Price) and the GST/HST Prod. Posting Group combination. The **Unit Price** on the Item Card, reduced by the GST/HST amount, is then entered in the **Unit Price Excl. GST/HST** field in the sales lines. For more information, see [Using GST/HST Business Posting Groups and Customer Price Groups](finance-work-with-vat.md#using-vat-business-posting-groups-and-customer-price-groups).|  
|Enabled|Enabled|The **Unit Price** on the Item Card is copied to **Unit Price Incl. GST/HST** field on the sales lines.|

#### <a name="using-vat-business-posting-groups-and-customer-price-groups" />Using GST/HST business posting groups and customer price groups

If you want prices to include GST/HST, you can use GST/HST business posting groups to calculate the amount based on the GST/HST posting setup for the group. For more information, see [Set up GST/HST business posting groups](finance-setup-vat.md#set-up-vat-business-posting-groups).

Depending on what you want to do, you can assign a GST/HST business posting group to customers or sales documents in the following ways:

* To use the same GST/HST rate for all customers, you can choose a group in the **GST/HST Business Posting Group (Price)** field on the **Sales & Receivables Setup** page.
* To use a GST/HST rate for a specific customer, you can choose a group in the **GST/HST Business Posting Group (Price)** field on the **Customer Card** page. 
* To use a GST/HST rate for a specific of customers, you can choose a group in the **GST/HST Business Posting Group (Price)** field on the **Customer Price Group** page. For example, this is useful when you want a price to apply to all customers in a certain geographical region or a specific industry.
* On all sales documents in the **GST/HST Business Posting Group** field. The GST/HST amount specified for the group is used only for the document you're currently working on.

> [!NOTE]
> If you do not specify a group in the **GST/HST Business Posting Group (Price)** field GST/HST will not be included in prices.

#### <a name="examples" />Examples

Factors such as the country or region you're selling in, or the type of industries you sell to, can impact the amount of GST/HST that you must account for. For example, a restaurant might charge 6% GST/HST for meals that are eaten in-house, and 17% for takeaway. To accomplish that, you create a GST/HST business posting group (price) for in-house and one for takeaway.

## <a name="working-with-vat-date" />Working with GST/HST Date

### <a name="vat-date-in-documents" />GST/HST Date in documents

When you create new sales or purchase documents, the **GST/HST Date** will be based on the setting in the **Default GST/HST Date** field on the **General Ledger Setup** page. This default value can be the same as **Posting Date** or **Document Date**. If you need a different GST/HST date, you can manually change the value in the **GST/HST Date** field. When you post the document, the **GST/HST Date** will be shown on the posting document and on the GST/HST and G/L entries.

> [!NOTE]
> If the **GST/HST Date** field isn't available on your documents or journals, that means that **Do not use GST/HST Date functionality** is chosen in the **GST/HST Date Usage** field on the **General Ledger Setup** page.  

> [!IMPORTANT]
> If you configure **Control GST/HST Period** in the **General Ledger Setup** as **Block posting within closed period**, or **Block posting within closed and warn for released period**, you can post document or journal only if the date in the **GST/HST Date** field is not in a closed period in **GST/HST Return Periods**. Even if the period in **GST/HST Return Periods** is open, you might get a warning based on the **GST/HST Return Status** and configuration in the **Control GST/HST Period**.

> [!IMPORTANT]
> You can prevent or allow posting of the **GST/HST Date** for specific data range, using the **Allow Posting From** and **Allow Posting To** fields in the **General Ledger Setup** and the **User Setup**.  

> [!NOTE]
> If you leave the **GST/HST Date** blank, [!INCLUDE [prod_short](includes/prod_short.md)] will use your default setup from **Default GST/HST Date** in the **General Ledger Setup** as a **GST/HST Date** in the posted transaction.  

### <a name="modifying-the-vat-date-in-posted-entries" />Modifying the GST/HST Date in posted entries

If needed, you can change the GST/HST date posted documents. To change the date in the **GST/HST Date** field for posted documents, follow these steps:

1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **GST/HST Entries**, and then choose the related link. 
2. Find the entry with wrong GST/HST date.  
3. Choose the **Edit list** action, and then enter the correct date in the **GST/HST Date** field.  
4. When you close the page, the GST/HST date will change in related **G/L Entries** and in the posted document.  

> [!NOTE]
> You can change the **GST/HST Date** field in **GST/HST Entries** only if your current date is not in a closed GST/HST return period. Even if the period in the **GST/HST Return Periods** field is open, you might get a warning based on the **GST/HST Return Status**.  

> [!NOTE]
> If your document has more than one **GST/HST Entry**, you only need to change the value in the **GST/HST Date** field in one entry related to the document. To keep entries consistent, [!INCLUDE[prod_short](includes/prod_short.md)] automatically changes the GST/HST date in GST/HST entries related to this transaction. [!INCLUDE [prod_short](includes/prod_short.md)] will update the **GST/HST Date** in other tables (GL Entries and documents), but only related to this transaction.  

## <a name="correcting-vat-amounts-manually-on-sales-and-purchase-documents" />Correcting GST/HST amounts manually on sales and purchase documents

You can make corrections to posted GST/HST entries so that you can change the total sales or purchase GST/HST amounts without changing the GST/HST base. For example, if you receive an invoice from a vendor with an incorrect GST/HST amount.  

Although you may have set up one or more combinations to handle import GST/HST, you must set up at least one GST/HST product posting group. For example, you can name it **CORRECT** for correction purposes, unless you can use the same general ledger account in the **Purchase GST/HST Account** field on the GST/HST posting setup line. For more information, see [Setting Up to Calculations and Posting Methods for GST/HST](finance-setup-vat.md).

If a payment discount has been calculated based on an invoice amount that includes GST/HST, you revert the payment discount part of the GST/HST amount when the payment discount is granted. Note that you must activate the **Adjust for Payments Disc.** field in both the general ledger setup in general and the GST/HST posting setup for specific combinations of a GST/HST business posting group and a GST/HST product posting group.  

### <a name="to-set-the-system-up-for-manual-vat-entry-in-sales-documents" />To set the system up for manual GST/HST entry in sales documents
The following describes how to enable manual GST/HST changes on sales documents. The steps are similar on the **Purchases & Payables Setup** page.

1. On the **General Ledger Setup** page, specify a **Max. GST/HST Difference Allowed** between the amount calculated by application and the manual amount.  
2. On the **Sales & Receivables Setup** page, place a check mark in the **Allow GST/HST Difference** field.  

### <a name="to-adjust-vat-for-a-sales-document" />To adjust GST/HST for a sales document

1. Open the relevant sales order.  
2. Choose the **Statistics** action.  
3. On the **Invoicing** FastTab, choose the value in the **No. of Tax Lines** field.
4. Edit the **GST/HST Amount** field.   

> [!NOTE]  
> The total GST/HST amount for the invoice, grouped by GST/HST identifier, is displayed in the lines. You can manually adjust the amount in the **GST/HST Amount** field on the lines for each GST/HST identifier. When you modify the **GST/HST Amount** field, application checks to ensure that you have not changed the GST/HST by more than the amount you have specified as the maximum difference allowed. If the amount is outside the range of the **Max. GST/HST Difference Allowed**, a warning will be displayed stating the maximum allowed difference. You will be unable to proceed until the amount is adjusted to within the acceptable parameters. Click **OK** and enter another **GST/HST Amount** that is within the allowed range. If the GST/HST difference is equal to or lower than the maximum allowed, the GST/HST will be divided proportionally among the document lines that have the same GST/HST identifier.  

## <a name="calculating-vat-manually-using-journals" />Calculating GST/HST manually using journals
You can also adjust GST/HST amounts in general, sales, and purchase journals. For example, you might need to do this when you enter a vendor invoice in your journal and there is a difference between the GST/HST amount that [!INCLUDE[prod_short](includes/prod_short.md)] calculated and the GST/HST amount on the vendor's invoice.  

### <a name="to-set-the-system-up-for-manual-vat-entry-in-a-general-journals" />To set the system up for manual GST/HST entry in a general journals
You must perform the following steps before you manually enter GST/HST in a general journal.  

1. On the **General Ledger Setup** page, specify a **Max. GST/HST Difference Allowed** between the amount calculated by application and the manual amount.  
2. On the **General Journal Templates** page, choose the **Allow GST/HST Difference** check box for the relevant journal.  

### <a name="to-set-the-system-up-for-manual-vat-entry-in-a-sales-and-purchase-journals" />To set the system up for manual GST/HST entry in a sales and purchase journals

You must perform the following steps before you manually enter GST/HST in a sales or purchase journal.

1. On the **Purchases & Payables Setup** page, choose the **Allow GST/HST Difference** check box.  
2. Repeat step 1 for the **Sales & Receivables Setup** page.
3. After you complete the setup described above, you can adjust the **GST/HST Amount** field on the general journal line, or the **Bal. GST/HST Amount** field on the sales or purchase journal line. [!INCLUDE[prod_short](includes/prod_short.md)] will check that the difference is not greater than the specified maximum.  

> [!NOTE]  
> If the difference is greater, a warning will be displayed stating the maximum allowed difference. To continue, you must adjust the amount. Choose **OK** and then enter an amount that is within the allowed range. If the GST/HST difference is equal to or lower than the maximum allowed, [!INCLUDE[prod_short](includes/prod_short.md)] will show the difference in the **GST/HST Difference** field.  

## <a name="posting-import-vat-with-purchase-invoices" />Posting Import GST/HST with Purchase Invoices
Instead of using journals to post an import GST/HST invoice, you can use a purchase invoice.  

### <a name="to-set-up-purchasing-for-posting-import-vat-invoices" />To set up purchasing for posting import GST/HST invoices

1. Set up a vendor card for the import authority that sends you the import GST/HST invoice. The **Gen. Bus. Posting Group** and **GST/HST Bus. Posting Group** must be set up in the same way as the general ledger account for the import GST/HST.  
2. Create a **Gen. Product Posting Group** for the import GST/HST and set up an import GST/HST **Def. GST/HST Product Posting Group** for the related **Gen. Product Posting Group**.  
3. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Chart of Accounts**, and then choose the related link.  
4. Select the import GST/HST general ledger account, and then choose the **Edit** action.  
5. On the **Posting** FastTab, select the **Gen. Prod. Posting Group** setup for import GST/HST. [!INCLUDE[prod_short](includes/prod_short.md)] automatically fills in the **GST/HST Prod. Posting Group** field.  
6. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **General Posting Setup**, and then choose the related link.  
7. Create a combination of the **Gen. Bus. Posting Group** for the GST/HST authority and the **Gen. Prod. Posting Group** for import GST/HST. For this new combination, in the **Purchase Account** field, choose the import GST/HST general ledger account.  

### <a name="to-create-a-new-invoice-for-the-import-authority-vendor-once-you-have-completed-the-setup" />To create a new invoice for the import authority vendor once you have completed the setup

1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Purchase Invoices**, and then choose the related link.  
2. Create a new purchase invoice.  
3. In the **Buy-from Vendor No.** field, choose the import authority vendor, and then choose the **OK** button.  
4. In the purchase line, in the **Type** field, choose **G/L Account**, and in the **No.** field, choose the import GST/HST general ledger account.  
5. In the **Quantity** field, type **1**.  
6. In the **Direct Unit Cost Excl. GST/HST** field, specify the GST/HST amount.  
7. Post the invoice.  

## <a name="processing-certificates-of-supply" />Processing certificates of supply

When you sell goods to a customer in another EU country/region, you must send the customer a certificate of supply that the customer must sign and return to you. The following procedures are for processing certificates of supply for sales shipments, but the same steps apply for service shipments of items, and return shipments to vendors.  

### <a name="to-view-certificate-of-supply-details" />To view certificate of supply details
1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Posted Sales Shipments**, and then choose the related link.  
2. Choose the relevant sales shipment to a customer in another EU country/region.  
3. Choose **Certificate of Supply Details**.  
4. By default, if the **Certificate of Supply Required** check box is selected for GST/HST Posting Group setup for the customer, the **Status** field is set to **Required**. You can update the field to indicate whether the customer has returned the certificate.  

> [!Note]  
>  If the GST/HST Posting Group setup does not have the **Certificate of Supply Required** check box selected, then a record is created and the **Status** field is set to **Not Applicable**. You can update the field to reflect the correct status information. You can manually change the status from **Not Applicable** to **Required**, and from **Required** to **Not Applicable** as needed.  

   When you update the **Status** field to **Required**, **Received**, or **Not Received**, a certificate is created.  

> [!TIP]  
>  You can use the **Certificates of Supply** page to get a view of the status of all posted shipments for which a certificate of supply has been created.  

5. Choose **Print Certificate of Supply**.  

> [!Note]  
>  You can preview or print the document. When you choose **Print Certificate of Supply** and print the document, the **Printed** check box is automatically selected. In addition, if not already specified, the status of the certificate is updated to **Required**. If needed, you include the printed certificate with the shipment.  

### <a name="to-print-a-certificate-of-supply" />To print a certificate of supply

1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Posted Sales Shipments**, and then choose the related link.  
2. Choose the relevant sales shipment to a customer in another EU country/region.  
3. Choose the **Print Certificate of Supply** action.  

> [!NOTE]  
>  Alternatively, you can print a certificate from the **Certificate of Supply** page.  

4. To include information from the lines on the shipment document in the certificate, select the **Print Line Details** check box.  
5. Choose the **Create Certificates of Supply if Not Already Created** check box to have [!INCLUDE[prod_short](includes/prod_short.md)] create certificates for posted shipments that do not have one at the moment of execution. When you choose the check box, new certificates will be created for all posted shipments that do not have certificates within the selected range.  
6. By default, the filter settings are for the shipment document that you have selected. Fill in the filter information to select a specific certificate of supply that you want to print.  
7. On the **Certificate of Supply** page, choose the **Print** action to print the report, or choose the **Preview** action to view it on the screen.  

> [!Note]  
> The **Certificate of Supply Status** field and the **Printed** field are updated for the shipment on the **Certificates of Supply** page.  

8. Send the printed certificate of supply to the customer for signature.  

### <a name="to-update-the-status-of-a-certificate-of-supply-for-a-shipment" />To update the status of a certificate of supply for a shipment

1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Posted Sales Shipments**, and then choose the related link.  
2. Choose the relevant sales shipment to a customer in another EU country/region.  
3. In the **Status** field, choose the relevant option.  

   If the customer has returned the signed certificate of supply, choose **Received**. The **Receipt Date** field is updated. By default, the receipt date is set to the current work date.  

   You can modify the date to reflect the date that you received the customer's signed certificate of supply. You can also add a link to the signed certificate using standard [!INCLUDE[prod_short](includes/prod_short.md)] linking.  

   If the customer does not return the signed certificate of supply, choose **Not Received**. You must then send the customer a new invoice that includes GST/HST, because the original invoice will not be accepted by the tax authority.  

To view a group of certificates, you start from the **Certificates of Supply** page, and then update the information about the status of outstanding certificates as you receive them back from your customers. This can be useful when you want to search for all certificates that have a certain status, for example, **Required**, for which you want to update their status to **Not Received**.  

### <a name="to-update-the-status-of-a-group-of-certificates-of-supply" />To update the status of a group of certificates of supply

1. Choose the ![Lightbulb that opens the Tell Me feature.](media/ui-search/search_small.png "Tell me what you want to do") icon, enter **Certificates of Supply**, and choose the related link.  
2. Filter the **Status** field to the value that you want in order to create the list of certificates that you want to manage.  
3. To update the status information, choose **Edit List**.  
4. In the **Status** field, choose the relevant option.  

   If the customer has returned the signed certificate of supply, choose **Received**. The **Receipt Date** field is updated. By default, the receipt date is set to the current work date.  

   You can modify the date to reflect the date that you received the signed the certificate of supply. You can also add a link to the signed certificate using standard [!INCLUDE[prod_short](includes/prod_short.md)] document linking.  

> [!NOTE]
> You cannot create a new certificate of supply on the **Certificate of Supply** page when you navigate to it using this procedure. To create a certificate for a shipment that was not set up to require one, open the posted sales shipment, and use either of two procedures described above:  
>
> * To manually create a certificate of supply certificate  
> * To print a certificate of supply.

## <a name="see-related-microsoft-trainingtrainingpathsprocess-vat-dynamics-365-business-central" />See related [Microsoft training](/training/paths/process-vat-dynamics-365-business-central/)

## <a name="see-also" />See Also

[Setting Up Calculations and Posting Methods for GST/HST](finance-setup-vat.md)  
[Report GST/HST to a Tax Authority](finance-how-report-vat.md)  
[Validate a VAT Registration Number](finance-how-validate-vat-registration-number.md)  

[!INCLUDE[footer-include](includes/footer-banner.md)]
