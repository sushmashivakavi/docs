## PRODUCTS/SERVICES

List of product names and product codes

@foreach($services as $key => $name)
@if ($loop->index == 0)
| Product Code | Product Name |
| ---- | ---- |
@endif
| {{ $key }} | {{ $name }} |
@endforeach
