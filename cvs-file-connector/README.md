---
description: CSV (RFC 4180) files using a .NET connector installed at the customer premises
---

# CVS File Connector

Use the CSV file connector in case you want to exchange new and changed orders and order responses using the Tradecloud proprietary CSV format and shared folders on your on premise server as transport.

<table>
  <thead>
    <tr>
      <th style="text-align:left"></th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Data Format</td>
      <td style="text-align:left"><a href="https://tools.ietf.org/html/rfc4180">RFC 4180</a>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Message types</td>
      <td style="text-align:left">Order (new and changed), Order response (new and changed)</td>
    </tr>
    <tr>
      <td style="text-align:left">Specifications</td>
      <td style="text-align:left">
        <p><a href="csv-buyer-specification.md">CVS Buyer Specification</a>
        </p>
        <p><a href="csv-supplier-specification.md">CSV Supplier Specification</a> 
          <br
          />(Gmail/GSuite account and access authorization required)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Transport</td>
      <td style="text-align:left">Shared folders on your on premise server</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="csv-file-connector-requirements.md">Requirements</a>
      </td>
      <td style="text-align:left">On premise installation, .NET 4.5 framework, outbound tcp/ip port 5670</td>
    </tr>
    <tr>
      <td style="text-align:left">Availability</td>
      <td style="text-align:left">Available for buyer and supplier sides</td>
    </tr>
  </tbody>
</table>