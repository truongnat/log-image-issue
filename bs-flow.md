### Confirm flow


**Data sample:**
```


- endpoint: /infra/volumes/

{
  "next": "http://api.example.org/accounts/?page=4",
  "previous": "http://api.example.org/accounts/?page=2",
  "count": 123,
  "results": [
    {
      "create_from": {
        "image": "046b6c7f-0b8a-43b9-b35d-6489e6daee91",
        "volume_type": "046b6c7f-0b8a-43b9-b35d-6489e6daee91",
        "snapshot": "046b6c7f-0b8a-43b9-b35d-6489e6daee91"
      },
      "size": 164,
      "encrypted": true,
      "name": "name",
      "description": "description",
      "cloud_object_id": "cloud_object_id",
      "id": "046b6c7f-0b8a-43b9-b35d-6489e6daee91",
      "bootable": true,
      "status": ""
    }
  ]
}

```

```


- endpoint: /infra/volume-type/

{
  "count": 123,
  "next": "http://api.example.org/accounts/?page=4",
  "previous": "http://api.example.org/accounts/?page=2",
  "results": [
    {
      "id": "f2341826-c843-4591-8631-636a1b9f9dca",
      "display_name": "VolumeType(f2341826-c843-4591-8631-636a1b9f9dca)",
      "created_at": "2022-06-16T02:01:47.988Z",
      "updated_at": "2022-06-16T02:01:47.988Z",
      "cloud_object_id": "f2341826-c843-4591-8631-636a1b9f9dca",
      "disk_type": "HDD",
      "speed": "Up to 10k IOPS",
      "name": "rbd-1",
      "description": "Ceph HDD",
      "disabled_reason": "",
      "state": "up",
      "status": "enabled",
      "zone": "2492cc60-9f4d-45ef-a0d6-74541f98714a"
    }
  ]
}


```


```

- endpoint: /organization/zones/

{
  "next": "http://api.example.org/accounts/?page=4",
  "previous": "http://api.example.org/accounts/?page=2",
  "count": 123,
  "results": [
    {
      "name": "name",
      "description": "description",
      "id": "046b6c7f-0b8a-43b9-b35d-6489e6daee91",
      "display_name": "display_name",
      "region": {
        "name": "name",
        "description": "description",
        "id": "046b6c7f-0b8a-43b9-b35d-6489e6daee91",
        "display_name": "display_name",
        "url": "http://example.com/aeiou"
      },
      "url": "http://example.com/aeiou"
    }
  ]
}

```




```

- endpoint: /organization/regions/
{
  "next": "http://api.example.org/accounts/?page=4",
  "previous": "http://api.example.org/accounts/?page=2",
  "count": 123,
  "results": [
    {
      "name": "name",
      "description": "description",
      "id": "046b6c7f-0b8a-43b9-b35d-6489e6daee91",
      "display_name": "display_name",
      "url": "http://example.com/aeiou"
    }
  ]
}

```


### Confirm flow:

Lấy tên zone và region:

- Step 1: Từ data của _/infra/volumes/_ có được id của _volume_type_ ở <create_from.volume_type>.
- Step 2: Truy vấn tiếp vào data của _/infra/volume-type/_ ( sẽ lấy đc zone id ).
- Step 3: Có zone id ở step 2 sẽ truy vấn tiếp vào data của __/organization/zones/_ và lấy được data của zone và regions .
