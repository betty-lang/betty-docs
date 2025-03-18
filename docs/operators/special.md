# Special Operators  

Betty provides special operators for handling ranges and list indexing efficiently.  

<table style="border-collapse: collapse; width: 100%;">
  <thead>
    <tr>
      <th style="width: auto;">Feature</th>
      <th style="width: auto;">Syntax</th>
      <th style="width: auto;">Description</th>
      <th style="width: auto;">Example Usage</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Range</strong></td>
      <td><code style="white-space: nowrap;">[start..end]</code></td>
      <td>Defines a range of values starting from <code>start</code>, incrementing by 1, and stopping before <code>end</code>. Internally calls <code>range()</code> function.</td>
      <td><code style="white-space: nowrap;">[1..4]</code> → <code style="white-space: nowrap;">[1, 2, 3]</code></td>
    </tr>
    <tr>
      <td><strong>List Indexing</strong></td>
      <td><code style="white-space: nowrap;">listvar[indexer]</code></td>
      <td>Accesses elements within a list using an index, which can be a number, variable, or function call.</td>
      <td><code style="white-space: nowrap;">a = [1, 2, 3];</code> <code style="white-space: nowrap;">print(a[0]);</code> → <code style="white-space: nowrap;">1</code></td>
    </tr>
  </tbody>
</table>