# API Mobile xúc tiến đầu tư

## API: get-geojson-country-by-code

## Mô tả
sử dụng để lấy danh sách các khu vực con (children) của một mã khu vực cụ thể.

### Đầu vào
- **`code`** (string): 
  - Mã khu vực (Code Country) cần tìm các khu vực con.
  - Ví dụ: `code = "001053"`.

### Đầu ra
- **`List<CountryGeoJsonDto>`**:
  - Một danh sách các đối tượng `CountryGeoJsonDto`, mỗi đối tượng đại diện cho một khu vực con của mã đầu vào.
  - Mỗi phần tử trong danh sách bao gồm:
    - **`IdCountry`**: ID của khu vực (kiểu `Guid`).
    - **`CodeCountry`**: Mã khu vực (kiểu `string`).
    - **`Geometry`**: Dữ liệu hình học (GeoJSON) của khu vực.

### Ví dụ sử dụng

### Ví dụ sử dụng
```http
GET /children/get-geojson-country-by-code?code=001053
```
#### Đầu ra:
```json
[
    {
        "IdCountry": "123e4567-e89b-12d3-a456-426614174000",
        "CodeCountry": "001053001",
        "Geometry": {
            "type": "Polygon",
            "coordinates": [[[102.0, 0.0], [103.0, 1.0], [104.0, 0.0], [102.0, 0.0]]]
        }
    },
    {
        "IdCountry": "123e4567-e89b-12d3-a456-426614174001",
        "CodeCountry": "001053002",
        "Geometry": {
            "type": "Polygon",
            "coordinates": [[[100.0, 0.0], [101.0, 1.0], [102.0, 0.0], [100.0, 0.0]]]
        }
    }
]
````

## API: `get-country-by-level-or-code`

## Mô tả
Sử dụng để lấy danh sách các quốc gia hoặc khu vực dựa trên mã khu vực (`code`) hoặc cấp độ (`level`).

### Đầu vào
- **`code`** (string): 
  - Mã khu vực (Code Country) để lọc danh sách quốc gia/khu vực.
  - Ví dụ: `code = "001053"`.
- **`level`** (int): 
  - Cấp độ của quốc gia/khu vực cần lấy.
  - Ví dụ: `level = 2`.

### Đầu ra
- **`List<CountryDto>`**:
  - Một danh sách các đối tượng `CountryDto`, mỗi đối tượng đại diện cho một quốc gia hoặc khu vực.
  - Mỗi phần tử trong danh sách bao gồm:
    - **`Id`**: ID của quốc gia/khu vực (kiểu `Guid`).
    - **`Code`**: Mã quốc gia/khu vực (kiểu `string`).
    - **`Name`**: Tên quốc gia/khu vực (kiểu `string`).
    - **`Level`**: Cấp độ của quốc gia/khu vực (kiểu `int`).
	- **`Id`**: ID của quốc gia/khu vực (kiểu `Guid`).
	- **`isDeleted`**: Trạng thái xóa của quốc gia/khu vực (kiểu `bool`).
	- **`name`**: Tên của quốc gia/khu vực (kiểu `string`).
	- **`description`**: Mô tả chi tiết về quốc gia/khu vực (kiểu `string`).
	- **`level`**: Cấp độ của quốc gia/khu vực (kiểu `int`).
	   - Ví dụ:
		 - `1`: Tỉnh/thành phố.
		 - `2`: Quận/huyện.
		 - `3`: Xã/phường.
	- **`type`**: Loại của quốc gia/khu vực (kiểu `string`).
	   - Ví dụ: "Quốc gia", "Tỉnh", "Huyện", "Xã".
	- **`code`**: Mã quốc gia/khu vực (kiểu `string`).
	- **`search`**: Chuỗi tìm kiếm liên quan đến quốc gia/khu vực (kiểu `string`).
	- **`fullCode`**: Mã đầy đủ của quốc gia/khu vực, bao gồm cả mã cha
	


#### Đầu vào:
#### Ví dụ sử dụng
```http
GET /get-country-by-level-or-code?code=001053&level=2
```
#### Đầu ra:
```json
[
    {
      "isDeleted": false,
      "name": "Bến Tre",
      "description": "Thành phố",
      "level": 2,
      "type": "district",
      "code": "001053001",
      "search": "thanh pho ben tre 001053001",
      "fullCode": "001053001",
      "lastModificationTime": null,
      "lastModifierId": null,
      "creationTime": "2020-12-02T02:55:38.203Z",
      "creatorId": null,
      "id": "ce17ac14-659a-6ff2-82d1-39f9338d4cdb"
    },
    {
      "isDeleted": false,
      "name": "Châu Thành",
      "description": "Huyện",
      "level": 2,
      "type": "district",
      "code": "001053002",
      "search": "huyen chau thanh 001053002",
      "fullCode": "001053002",
      "lastModificationTime": null,
      "lastModifierId": null,
      "creationTime": "2020-12-02T02:55:38.299Z",
      "creatorId": null,
      "id": "aaebfeca-9bb1-6f83-b692-39f9338d4d3b"
    }
]
````

## API: `get-detail-country-view`

### Mô tả
Sử dụng để lấy thông tin chi tiết của một quốc gia hoặc khu vực dựa trên mã khu vực (`code`) và loại dự án (`type`).

---

### Đầu vào
- **`code`** (string): 
  - Mã quốc gia hoặc khu vực cần lấy thông tin chi tiết.
  - Ví dụ: `code = "001053"`.

---

### Đầu ra
- **`DetailCountryDto`**:
  - Một đối tượng chứa thông tin chi tiết của quốc gia hoặc khu vực, bao gồm:
    - **`Id`**: ID của quốc gia/khu vực (kiểu `Guid`).
    - **`Code`**: Mã quốc gia/khu vực (kiểu `string`).
    - **`Name`**: Tên quốc gia/khu vực (kiểu `string`).
    - **`Acreage`**: Diện tích của quốc gia/khu vực (kiểu `double`).
    - **`Density`**: Mật độ dân số (kiểu `double`).
    - **`Population`**: Dân số (kiểu `int`).
    - **`Description`**: Mô tả quốc gia/khu vực (kiểu `string`).
    - **`Tags`**: Các thẻ liên quan (kiểu `string`).
    - **`CountProject`**: Số lượng dự án trong khu vực (kiểu `int`).
    - **`Location`**: Vị trí địa lý của quốc gia/khu vực (kiểu `string`).

---
#### Ví dụ sử dụng
### Đầu vào
```http
GET /get-detail-country-view?code=001053003
```
#### Đầu ra:
```json
 {
    "name": "Huyện Chợ Lách",
    "countProject": 16,
    "code": "001053003",
    "acreage": 168.04,
    "population": "147.289 người",
    "density": 877,
    "description": "Huyện lỵ là thị trấn Chợ Lách nằm trên tỉnh lộ 57 cách thành phố Bến Tre 45 km về phía tây và cách thành phố Vĩnh Long 20 km về phía đông. Mật độ dân số : 877 người/km²",
    "tags": null,
    "location": {
      "lng": 106.14953625062691,
      "lat": 10.23412921805344
    },
    "id": "5705626b-446a-0013-1494-3a07f788d8dd"
  }

```


## API: get-main-object-by-filter

### Mô tả
API này được sử dụng để lọc và lấy danh sách các đối tượng chính dựa trên tham số GeoJSON và các tiêu chí khác.

### Đầu vào
- `param` (FilterParameter): Tham số lọc bao gồm:
  - `Searching` (string): Từ khóa tìm kiếm.
  - `Country` (string): Quốc gia.
  - `ProjectArea` (string): Khu vực dự án.
  - `Layer` (string): Lớp.
  - `District` (string): Quận.
  - `SubDistrict` (string): Phường.
  - `PlanToDo` (string): Kế hoạch.
  - `ProgressProject` (string): Tiến độ dự án.
  - `MinRange` (double): Phạm vi tối thiểu.
  - `MaxRange` (double): Phạm vi tối đa.
  - `MinRangeScale` (double): Tỷ lệ tối thiểu.
  - `MaxRangeScale` (double): Tỷ lệ tối đa.
  - `StatusProject` (string): Trạng thái dự án.
  - `SkipCount` (int): Số lượng bản ghi bỏ qua.
  - `MaxResultCount` (int): Số lượng bản ghi tối đa.

### Đầu ra
- Trả về đối tượng `MainDirectoryDto` bao gồm:
	- **`idDirectory`** (`string`):ID của thư mục chứa đối tượng chính.-

	- **`nameObject`** (`string`):Tên của đối tượng chính.

	- **`geometry`** (`object`):Dữ liệu hình học (GeoJSON) của đối tượng chính.
	   
	- **`properties`** (`object`):
	   - Thuộc tính hiển thị của đối tượng chính.
	   - Bao gồm:
		 - **`image2D`** (`string`): Hình ảnh 2D (nếu có), ví dụ: `null`.
		 - **`stroke`** (`string`): Màu đường viền, ví dụ: `"#a31ad5"`.
		 - **`strokeWidth`** (`int`): Độ dày đường viền, ví dụ: `2`.
		 - **`strokeOpacity`** (`float`): Độ trong suốt của đường viền, ví dụ: `1`.
		 - **`styleStroke`** (`string`): Kiểu đường viền, ví dụ: `null`.
		 - **`fill`** (`string`): Màu nền, ví dụ: `"#a31ad5"`.
		 - **`fillOpacity`** (`float`): Độ trong suốt của màu nền, ví dụ: `0.3`.

	- **`object3D`** (`object`):
	   - Dữ liệu 3D của đối tượng (nếu có), ví dụ: `null`.

	- **`district`** (`string`):
	   - Mã quận/huyện của đối tượng chính.
	   - Ví dụ: `"001053006"`.

	- **`wardDistrict`** (`string`):
	   - Mã phường/xã của đối tượng chính.
	   - Ví dụ: `"001053006015"`.

	- **`codeProject`** (`string`):
	   - Mã dự án liên quan đến đối tượng chính.
	   - Ví dụ: `"DA8689"`.

	- **`projectAreaCode`** (`string`):
	   - Mã khu vực dự án (nếu có), ví dụ: `""`.

	- **`tags`** (`object`):Các thẻ bổ sung liên quan đến đối tượng chính.

	- **`lastModificationTime`** (`string`):
		- Thời gian chỉnh sửa lần cuối của đối tượng.

	- **`lastModifierId`** (`string`):
		- ID của người chỉnh sửa lần cuối.

	- **`creationTime`** (`string`):
		- Thời gian tạo đối tượng.

	- **`creatorId`** (`string`):
		- ID của người tạo đối tượng.

	- **`id`** (`string`):
		- ID duy nhất của đối tượng chính.
  - `propertiesSettingDtos`: Danh sách cấu hình thuộc tính.
  

### Ví dụ
### Request
```http
GET /api/HTKT/ManagementData/get-main-object-by-filter
```

#### Response
```json
{
    "mainObjects": [
        {
		  "idDirectory": "9d7e8e52-7e6c-fb07-ae22-3a07fb23f941",
		  "nameObject": "Khu dân cư tập trung xã Bình Thắng",
		  "geometry": {
			"type": "MultiPolygon",
			"coordinates": [
			  [
				[
				  [
					106.71076202392578,
					10.211651802063045
				  ],
				  ...
				  [
					106.71076202392578,
					10.211651802063045
				  ]
				]
			  ]
			]
		  },
		  "properties": {
			"image2D": null,
			"stroke": "#a31ad5",
			"strokeWidth": 2,
			"strokeOpacity": 1,
			"styleStroke": null,
			"fill": "#a31ad5",
			"fillOpacity": 0.3
		  },
		  "object3D": null,
		  "district": "001053006",
		  "wardDistrict": "001053006015",
		  "codeProject": "DA8689",
		  "projectAreaCode": "",
		  "tags": {
			"typeData": "newMultipolygonByCountry"
		  },
		  "lastModificationTime": "2022-12-13T02:15:02.527Z",
		  "lastModifierId": "16d7eb2b-aa64-5d66-de79-39fe2d19a269",
		  "creationTime": "2022-12-06T20:42:52.051Z",
		  "creatorId": "16d7eb2b-aa64-5d66-de79-39fe2d19a269",
		  "id": "8518c600-77f9-4895-9e0f-3a07fb5a2913"
		}
    ],
    "propertiesSettingDtos": [
        {
		  "idDirectory": "8a9703ee-552f-750c-b005-3a0b7ca1a434",
		  "minZoom": 0,
		  "maxZoom": 0,
		  "image2D": null,
		  "object3D": "",
		  "texture3D": null,
		  "stroke": "#12a537",
		  "strokeWidth": 5,
		  "strokeOpacity": 1,
		  "styleStroke": "straightline",
		  "fill": "#12a537",
		  "fillOpacity": 0.3,
		  "tags": {
			"icon": "undefined"
		  },
		  "lastModificationTime": null,
		  "lastModifierId": null,
		  "creationTime": "2023-05-30T02:22:35.898Z",
		  "creatorId": "16d7eb2b-aa64-5d66-de79-39fe2d19a269",
		  "id": "9b303200-7d77-ccca-148e-3a0b7ca3b979"
		}
    ]
}
```

## API: get-list-note-layer

### Mô tả
API này được sử dụng để lấy danh sách các lớp ghi chú (note layer) với thông tin cấu hình.

### Đầu vào
- Không có tham số đầu vào.

### Đầu ra
- Trả về danh sách các lớp ghi chú bao gồm:
  - `Id`: ID của lớp ghi chú.
  - `IdDirectory`: ID thư mục chứa lớp ghi chú.
  - `Fill`: Màu nền.
  - `FillOpacity`: Độ trong suốt của màu nền.
  - `Stroke`: Màu viền.
  - `StrokeOpacity`: Độ trong suốt của màu viền.
  - `StrokeWidth`: Độ dày của viền.
  - `StyleStroke`: Kiểu viền.
  - `Image2D`: Hình ảnh 2D.
  - `Object3D`: Đối tượng 3D.
  - `Texture3D`: Kết cấu 3D.
  - `Name`: Tên lớp ghi chú.
  - `Tags`: Các thẻ liên quan.

### Ví dụ
#### Request
```http
GET /api/khaithac/khaiThacDirectory/get-list-note-layer
```

#### Response
```json

    [	{
            "id": "12345",
            "idDirectory": "dir001",
            "fill": "#8b5b5b",
            "fillOpacity": 0.3,
            "stroke": "#000000",
            "strokeOpacity": 1.0,
            "strokeWidth": 2,
            "styleStroke": "solid",
            "image2D": "image_url",
            "object3D": "object_3d_url",
            "texture3D": "texture_3d_url",
            "name": "Layer 1",
            "tags": {
                "public": true
            }
        },
        {
            "id": "67890",
            "idDirectory": "dir002",
            "fill": "#ffffff",
            "fillOpacity": 0.5,
            "stroke": "#ff0000",
            "strokeOpacity": 0.8,
            "strokeWidth": 1,
            "styleStroke": "dashed",
            "image2D": null,
            "object3D": null,
            "texture3D": null,
            "name": "Layer 2",
            "tags": {
                "public": false
            }
        }
	]
```

## API: get-list-area-async

### Mô tả
API này được sử dụng để lấy danh sách các khu vực dự án dựa trên các tiêu chí lọc.

### Đầu vào
- `input` (GetProjectAreaInput): Tham số lọc bao gồm:
  - `Filter` (string): Từ khóa tìm kiếm.
  - `Name` (string): Tên khu vực.
  - `CodeName` (string): Mã khu vực.
  - `Geometry` (GeoJSON): Hình học khu vực.
  - `Location` (string): Vị trí.
  - `UrlIcon` (string): URL biểu tượng.
  - `LinkUrlInfo` (string): URL thông tin.
  - `Order` (int): Thứ tự.
  - `ShortDescription` (string): Mô tả ngắn.
  - `Description` (string): Mô tả.
  - `Document` (string): Tài liệu.
  - `MaxResultCount` (int): Số lượng bản ghi tối đa.
  - `SkipCount` (int): Số lượng bản ghi bỏ qua.

### Đầu ra
- Trả về chuỗi JSON chứa danh sách các khu vực dự án và tổng số lượng.
	- **`Id`** (`Guid`):
	   - ID duy nhất của khu vực dự án.
	   - Thuộc tính này được kế thừa từ `ProjectAreaDto`.

	- **`Name`** (`string`):
	   - Tên của khu vực dự án.
	   - Ví dụ: `"Cụm công nghiệp Tân Thành Bình"`.

	- **`CodeName`** (`string`):
	   - Mã định danh của khu vực dự án.
	   - Ví dụ: `"cumcongnghieptanthanhbinh"`.

	- **`Geometry`** (`object`):
	   - Dữ liệu hình học (GeoJSON) của khu vực dự án.
	   - Bao gồm:
		 - **`type`** (`string`): Loại hình học, ví dụ `"MultiLineString"`.
		 - **`coordinates`** (`array`): Tọa độ của hình học, ví dụ:
		   ```json
		   [
			 [
			   [106.32404443282586, 10.210424282352664],
			   ...
			   [106.32404443282586, 10.210424282352664]
			 ]
		   ]
		   ```

	- **`Location`** (`string`):
	   - Vị trí của khu vực dự án (nếu có), ví dụ: `null`.

	- **`UrlIcon`** (`string`):
	   - URL của biểu tượng đại diện cho khu vực dự án.
	   - Ví dụ: `"https://map-xtdt.bentre.gov.vn/dataapp/image/e4028513-ac2d-4b41-b969-4fb21ee86097.png"`.

	- **`LinkUrlInfo`** (`string`):
	   - URL liên kết đến thông tin chi tiết của khu vực dự án (nếu có), ví dụ: `null`.

	- **`Order`** (`int`):
	   - Thứ tự hiển thị của khu vực dự án, ví dụ: `0`.

	- **`ShortDescription`** (`string`):
	   - Mô tả ngắn gọn về khu vực dự án (nếu có), ví dụ: `null`.

	- **`Description`** (`string`):
		- Mô tả chi tiết về khu vực dự án (nếu có), ví dụ: `null`.

	- **`Document`** (`string`):
		- Tài liệu liên quan đến khu vực dự án (nếu có), ví dụ: `null`.

	- **`ParentId`** (`Guid`):
		- ID của khu vực cha (nếu có), ví dụ: `null`.

	- **`TypeCategory`** (`string`):
		- Loại danh mục của khu vực dự án (nếu có), ví dụ: `null`.

	- **`ShowLabel`** (`bool`):
		- Trạng thái hiển thị nhãn của khu vực dự án (nếu có), ví dụ: `null`.

	- **`IsDeleted`** (`bool`):
		- Trạng thái xóa của khu vực dự án.
		- `true` nếu đã bị xóa, `false` nếu chưa bị xóa.

	- **`DeleterId`** (`Guid`):
		- ID của người đã xóa khu vực dự án (nếu có), ví dụ: `null`.

	- **`DeletionTime`** (`DateTime`):
		- Thời gian xóa khu vực dự án (nếu có), ví dụ: `null`.

	- **`LastModificationTime`** (`DateTime`):
		- Thời gian chỉnh sửa lần cuối của khu vực dự án (nếu có), ví dụ: `null`.

	- **`LastModifierId`** (`Guid`):
		- ID của người chỉnh sửa lần cuối (nếu có), ví dụ: `null`.

	- **`CreationTime`** (`DateTime`):
		- Thời gian tạo khu vực dự án.
		- Ví dụ: `"0001-01-01T00:00:00"`.

	- **`CreatorId`** (`Guid`):
		- ID của người tạo khu vực dự án (nếu có), ví dụ: `null`.

	- **`CountProject`** (`int`):
		- Số lượng dự án trong khu vực.
		- Ví dụ: `0`.

### Ví dụ
### Request
```http
GET /get-list-area-async?filter=AreaA&maxResultCount=1000&skipCount=0
```

#### Response
```json
{
    "totalCount": 2,
    "items": [
        {
		  "countProject": 0,
		  "name": "Cụm công nghiệp Tân Thành Bình",
		  "codeName": "cumcongnghieptanthanhbinh",
		  "geometry": {
			"type": "MultiLineString",
			"coordinates": [
			  [
				[
				  106.32404443282586,
				  10.210424282352664
				],
				...
				[
				  106.32404443282586,
				  10.210424282352664
				]
			  ]
			]
		  },
		  "location": null,
		  "urlIcon": "https://map-xtdt.bentre.gov.vn/dataapp/image/e4028513-ac2d-4b41-b969-4fb21ee86097.png",
		  "linkUrlInfo": null,
		  "order": 0,
		  "shortDescription": null,
		  "description": null,
		  "document": null,
		  "parentId": null,
		  "typeCategory": null,
		  "showLabel": null,
		  "isDeleted": false,
		  "deleterId": null,
		  "deletionTime": null,
		  "lastModificationTime": null,
		  "lastModifierId": null,
		  "creationTime": "0001-01-01T00:00:00",
		  "creatorId": null,
		  "id": "ab825c7b-ed95-7738-7cdc-3a0be908bad7"
		}
    ]
}
```

## API: get-category

## Mô tả
Sử dụng để lấy danh mục các thuộc tính mặc định (Properties Default) được cấu hình trong hệ thống.

---

### Đầu vào
- API không yêu cầu tham số đầu vào.

---

### Đầu ra
- **`Dictionary<string, object>`**:
  - Một đối tượng từ điển chứa các danh mục thuộc tính và danh sách các thuộc tính tương ứng.
  - Cấu trúc:
    - **ProjectPregress**: danh mục tiến độ dự án.
    - **TRANGTHAIDUAN**: danh mục trạng thái dự án.
	- **planTodo**: danh mục dự án.

---

### Ví dụ
#### Request
```http
GET /api/HTKT/PropertiesDefault/get-category
```

#### Response
```json
{
  "code": 200,
  "message": "",
  "data": {
        "planTodo": [
            {
                "label": "Dự án ưu tiên thu hút đầu tư",
                "code": "TRONGDIEMTHUHUTDAUTU"
            },
            {
                "label": "Dự án đang triển khai và tiếp tục thu hút đầu tư",
                "code": "DAVADANGDAUTU"
            },
            {
                "label": "Dự án đã đầu tư",
                "code": "DAANDAHOANTHIENDAUTU"
            }
        ],
        "ProjectPregress": [
            {
                "label": "Đang hoạt động",
                "code": "DANGHOATDONG"
            },
            {
                "label": "Đang triển khai",
                "code": "DANGTRIENKHAI"
            },
            {
                "label": "Đang tạm dừng",
                "code": "DANGTAMDUNG"
            },
            {
                "label": "Chưa hoạt động",
                "code": "CHUAHOATDONG"
            }
        ],
        "TRANGTHAIDUAN": [
            {
                "label": "Dự án chưa đầu tư",
                "code": "DUANCHUADAUTU"
            },
            {
                "label": "Dự án đã đầu tư",
                "code": "DUANDADAUTU"
            }
        ]
    }
}
```

## API: get-nation

## Mô tả
Sử dụng để lấy danh sách quốc gia.

---

### Đầu vào
- API không yêu cầu tham số đầu vào.

---

### Đầu ra
- **`Dictionary<string, object>`**:
  - Một đối tượng từ điển chứa các danh mục thuộc tính và danh sách các thuộc tính tương ứng.
  - Cấu trúc:
    - **id**: ID duy nhất (GUID) của đối tượng cần lấy thông tin.
    - **name**: Tên quốc gia.
	- **code**: code quốc gia.

---

### Ví dụ
#### Request
```http
GET /api/HTKT/PropertiesDefault/get-category
```

#### Response
```json
{
  "code": 200,
  "message": "",
  "data": [
        {
		  "id": "bfd13ebf-d484-4387-b572-b0255b175cec",
		  "name": "Việt Nam",
		  "code": "Việt Nam",
		  "checked": true,
		  "action": ""
		}
    ]
}
```


## API: get-response-index-modal-new-views

### Mô tả
API này được sử dụng để danh sách lĩnh vực và KCN,CCN cụm công nghiệp của thu hút đầu tư , đa và đang đầu tư.

### Đầu vào
Hàm không nhận tham số đầu vào trực tiếp.

### Đầu ra
- **`List<object>`**:
  - Một danh sách các đối tượng, mỗi đối tượng đại diện cho một loại dự án hoặc nhóm dự án.
  - Cấu trúc:
    - **`type`** (`string`): Loại dự án, ví dụ: `"TAMNHIHUONGDONG"`, `"TRONGDIEMTHUHUTDAUTU"`, `"DAVADANGDAUTU"`, `"DAANDAHOANTHIENDAUTU"`.
    - **`name`** (`string`): Tên của loại dự án.
    - **`listProjectArea`** (`List<ProjectArea>`): Danh sách các khu vực dự án (nếu có).
    - **`listGroupArea`** (`List<GroupArea>`): Danh sách các nhóm khu vực dự án (nếu có).

---

### Chi tiết các thuộc tính

#### 1. **`ProjectArea`**
- **`projectAreaChild`** (`List<ProjectArea>`): Danh sách các khu vực con (nếu có).
- **`name`** (`string`): Tên khu vực dự án.
- **`idProjectArea`** (`string`): ID của khu vực dự án.
- **`codeName`** (`string`): Mã định danh của khu vực dự án.
- **`urlIcon`** (`string`): URL của biểu tượng đại diện cho khu vực dự án.
- **`listDirectories`** (`List<Directory>`): Danh sách các thư mục liên quan đến khu vực dự án.

#### 2. **`GroupArea`**
- **`type`** (`string`): Loại nhóm khu vực, ví dụ: `"CUM"`, `"KHU"`, `"NGOAIKCNCCN"`.
- **`name`** (`string`): Tên nhóm khu vực.
- **`listProjectArea`** (`List<ProjectArea>`): Danh sách các khu vực dự án trong nhóm.

#### 3. **`Directory`**
- **`idDirectory`** (`string`): ID của thư mục.
- **`name`** (`string`): Tên của thư mục.
- **`count`** (`int`): Số lượng dự án trong thư mục.
- **`image`** (`string`): URL của hình ảnh đại diện cho thư mục.
- **`seacrch`** (`string`): Chuỗi tìm kiếm liên quan đến thư mục (nếu có).

---

#### Ví dụ
#### Request
```http
GET /HTKT/ProjectArea/get-response-index-modal-new-views
```

#### Response
```json
[
  {
    "Type": "TAMNHIHUONGDONG",
    "Name": "Bến Tre - tầm nhìn hướng đông",
    "ListProjectArea": [
      {
        "IdProjectArea": "12345",
        "Name": "Khu vực A",
        "CodeName": "AreaA",
        "UrlIcon": "https://example.com/iconA.png",
        "ListDirectories": [
          {
            "IdDirectory": "dir001",
            "Name": "Thư mục 1",
            "Count": 5,
            "image": "https://example.com/image1.png"
          }
        ]
      }
    ],
    "ListGroupArea": []
  },
  {
    "Type": "DAVADANGDAUTU",
    "Name": "Dự án đang triển khai và tiếp tục thu hút đầu tư",
    "ListProjectArea": [],
    "ListGroupArea": [
      {
        "Type": "KHU",
        "Name": "Khu công nghiệp",
        "ListProjectArea": [
          {
            "IdProjectArea": "67890",
            "Name": "Khu vực B",
            "CodeName": "AreaB",
            "UrlIcon": "https://example.com/iconB.png",
            "ListDirectories": []
          }
        ]
      }
    ]
  }
]
```

# API: get-number-object-by-IdDirectory-and-type

## Mô tả
Sử dụng để lấy Danh sách dự án của lĩnh vực trong KCN,CCN cụm công nghiệp

---

## Đầu vào
API yêu cầu các tham số sau:

1. **`idProjectArea`** (`string`):
   - ID của id của KCN,CCN cụm công nghiệp

2. **`id`** (`string`):
   - ID của lĩnh vực nào.

3. **`type`** (`string`):
   - Loại đối tượng.
   - Ví dụ: `"TRONGDIEMTHUHUTDAUTU", "DAVADANGDAUTU" và "TAMNHIHUONGDONG"`.

---

## Đầu ra
- **`Object`**:
  - Một đối tượng chứa thông tin chi tiết về đối tượng được lọc.
  - Cấu trúc:

### Chi tiết các thuộc tính của đối tượng trả về:
- **`idDirectory`** (`string`):
	- ID của thư mục chứa đối tượng.
	- Ví dụ: `"3572d80f-de05-5821-bb7a-3a07f1e4e673"`.

- **`nameObject`** (`string`):
	- Tên của đối tượng.
	- Ví dụ: `"Khu công nghiệp An Nhơn"`.

- **`geometry`** (`object`):
	- Dữ liệu hình học (GeoJSON) của đối tượng.
	- Bao gồm:
		- **`type`** (`string`): Loại hình học, ví dụ `"Polygon"`.
		- **`coordinates`** (`array`): Tọa độ của hình học.

- **`isCheckImplementProperties`** (`bool`):
	- Trạng thái kiểm tra thuộc tính của đối tượng.
	- Ví dụ: `true`.

- **`properties`** (`object`):
	- Thuộc tính hiển thị của đối tượng.
	- Bao gồm:
		- **`image2D`** (`string`): URL của hình ảnh 2D, ví dụ: `"https://map-xtdt.bentre.gov.vn/dataapp/image/1ccae489-bc16-4f5f-8ebb-279f3954dd54.png"`.
		- **`stroke`** (`string`): Màu đường viền, ví dụ: `"#864e0e"`.
		- **`strokeWidth`** (`int`): Độ dày đường viền, ví dụ: `2`.
		- **`strokeOpacity`** (`float`): Độ trong suốt của đường viền, ví dụ: `1`.
		- **`styleStroke`** (`string`): Kiểu đường viền, ví dụ: `"straightline"`.
		- **`fill`** (`string`): Màu nền, ví dụ: `"#864e0e"`.
		- **`fillOpacity`** (`float`): Độ trong suốt của màu nền, ví dụ: `0.3`.

- **`object3D`** (`object`):
	- Dữ liệu 3D của đối tượng (nếu có), ví dụ: `null`.

- **`tags`** (`object`):
	- Các thẻ liên quan đến đối tượng.
	- Ví dụ:
		```json
		{
		"typeData": "newMultipolygon"
		}
		```

- **`searchObject`** (`string`):
	- Chuỗi tìm kiếm liên quan đến đối tượng.
	- Ví dụ: `"khu cong nghiep an nhon"`.

- **`qrCodeObject`** (`string`):
	- Mã QR của đối tượng (nếu có), ví dụ: `""`.

- **`district`** (`string`):
	- Mã quận/huyện của đối tượng.
	- Ví dụ: `"001053008"`.

- **`wardDistrict`** (`string`):
	- Mã phường/xã của đối tượng.
	- Ví dụ: `"001053008015"`.

- **`codeProject`** (`string`):
	- Mã dự án liên quan đến đối tượng.
	- Ví dụ: `"DA51423"`.

- **`projectAreaCode`** (`string`):
	- Mã khu vực dự án (nếu có), ví dụ: `""`.

- **`lastModificationTime`** (`string`):
	- Thời gian chỉnh sửa lần cuối của đối tượng.
	- Ví dụ: `"2024-09-29T09:36:13.202Z"`.

- **`lastModifierId`** (`string`):
	- ID của người chỉnh sửa lần cuối.
	- Ví dụ: `"668a4542-15dd-5dc3-b2b3-3a11010cc61f"`.

- **`creationTime`** (`string`):
	- Thời gian tạo đối tượng.
	- Ví dụ: `"2023-06-21T03:48:45.441Z"`.

- **`creatorId`** (`string`):
	- ID của người tạo đối tượng.
	- Ví dụ: `"16d7eb2b-aa64-5d66-de79-39fe2d19a269"`.

- **`extraProperties`** (`object`):
	- Các thuộc tính bổ sung (nếu có), ví dụ: `{}`.

- **`concurrencyStamp`** (`string`):
	- Dấu hiệu đồng bộ hóa dữ liệu.
	- Ví dụ: `"9d15c015c249492dad69c5de0a635b45"`.

- **`id`** (`string`):
	- ID duy nhất của đối tượng.
	- Ví dụ: `"fb8c815a-27bb-2c22-7209-3a0bee3e8301"`.

---
#### Ví dụ
### Request
```http
GET /api/HTKT/ManagementData/get-number-object-by-IdDirectory-and-type?idProjectArea=&id=3572d80f-de05-5821-bb7a-3a07f1e4e673&type=TRONGDIEMTHUHUT
```

#### Response
```json
	{
	  "idDirectory": "3572d80f-de05-5821-bb7a-3a07f1e4e673",
	  "nameObject": "Khu công nghiệp An Nhơn",
	  "geometry": {
		"type": "Polygon",
		"coordinates": [
		  [
			[
			  106.5642958956085,
			  9.867865674642317
			],
			...
			[
			  106.5642958956085,
			  9.867865674642317
			]
		  ]
		]
	  },
	  "isCheckImplementProperties": true,
	  "properties": {
		"image2D": "https://map-xtdt.bentre.gov.vn/dataapp/image/1ccae489-bc16-4f5f-8ebb-279f3954dd54.png",
		"stroke": "#864e0e",
		"strokeWidth": 2,
		"strokeOpacity": 1,
		"styleStroke": "straightline",
		"fill": "#864e0e",
		"fillOpacity": 0.3
	  },
	  "object3D": null,
	  "tags": {
		"typeData": "newMultipolygon"
	  },
	  "searchObject": "khu cong nghiep an nhon",
	  "qrCodeObject": "",
	  "district": "001053008",
	  "wardDistrict": "001053008015",
	  "codeProject": "DA51423",
	  "projectAreaCode": "",
	  "lastModificationTime": "2024-09-29T09:36:13.202Z",
	  "lastModifierId": "668a4542-15dd-5dc3-b2b3-3a11010cc61f",
	  "creationTime": "2023-06-21T03:48:45.441Z",
	  "creatorId": "16d7eb2b-aa64-5d66-de79-39fe2d19a269",
	  "extraProperties": {},
	  "concurrencyStamp": "9d15c015c249492dad69c5de0a635b45",
	  "id": "fb8c815a-27bb-2c22-7209-3a0bee3e8301"
	}
```

## API get-object-view

## Mô tả
Get thông tin chi tiết của dự án.

### Mô tả
Hàm được sử dụng để lấy thông tin chi tiết về một đối tượng cụ thể dựa trên ID.

### Đầu vào
- **`id`** (string): ID duy nhất (GUID) của đối tượng cần lấy thông tin.

## Đầu ra
- **`Object`**:
  - Một đối tượng chứa thông tin chi tiết về đối tượng được yêu cầu.
  - Cấu trúc:

### Chi tiết các thuộc tính của đối tượng trả về:

- **`id`** (`string`):
	- ID duy nhất của đối tượng.
	- Ví dụ: `"fb8c815a-27bb-2c22-7209-3a0bee3e8301"`.

- **`nameObject`** (`string`):
	- Tên của đối tượng.
	- Ví dụ: `"Khu công nghiệp An Nhơn"`.

- **`geometry`** (`object`):
	- Dữ liệu hình học (GeoJSON) của đối tượng.
	- Bao gồm:
		- **`type`** (`string`): Loại hình học, ví dụ `"Polygon"`.
		- **`coordinates`** (`array`): Tọa độ của hình học.

- **`listProperties`** (`List<object>`):
	- Danh sách các thuộc tính của đối tượng.
	- Mỗi thuộc tính bao gồm:
		- **`nameProperties`** (`string`): Tên thuộc tính, ví dụ `"Tên dự án"`.
		- **`codeProperties`** (`string`): Mã thuộc tính, ví dụ `"Name"`.
		- **`typeProperties`** (`string`): Loại thuộc tính, ví dụ `"string"`, `"list"`, `"geojson"`, `"image"`, `"video"`, `"vr360"`.
		- **`isShow`** (`bool`): Trạng thái hiển thị thuộc tính.
		- **`isView`** (`bool`): Trạng thái xem thuộc tính.
		- **`defalutValue`** (`string`): Giá trị mặc định của thuộc tính.
		- **`orderProperties`** (`int`): Thứ tự hiển thị của thuộc tính.
		- **`typeSystem`** (`int`): Loại hệ thống của thuộc tính.

- **`idDirectory`** (`string`):
	- ID của thư mục chứa đối tượng.
	- Ví dụ: `"3572d80f-de05-5821-bb7a-3a07f1e4e673"`.

- **`properties`** (`object`):
	- Thuộc tính hiển thị của đối tượng.
	- Bao gồm:
		- **`image2D`** (`string`): URL của hình ảnh 2D (nếu có), ví dụ: `null`.
		- **`stroke`** (`string`): Màu đường viền, ví dụ: `"#864e0e"`.
		- **`strokeWidth`** (`int`): Độ dày đường viền, ví dụ: `2`.
		- **`strokeOpacity`** (`float`): Độ trong suốt của đường viền, ví dụ: `1`.
		- **`styleStroke`** (`string`): Kiểu đường viền, ví dụ: `null`.
		- **`fill`** (`string`): Màu nền, ví dụ: `"#864e0e"`.
		- **`fillOpacity`** (`float`): Độ trong suốt của màu nền, ví dụ: `0.3`.

- **`object3D`** (`object`):
	- Dữ liệu 3D của đối tượng (nếu có), ví dụ: `null`.

- **`tags`** (`object`):
	- Các thẻ liên quan đến đối tượng.
	- Ví dụ:
		```json
		{
		"typeData": "newMultipolygon"
		}
		```

- **`isCheckImplementProperties`** (`bool`):
	- Trạng thái kiểm tra thuộc tính của đối tượng.
	- Ví dụ: `true`.

- **`qrCodeObject`** (`string`):
	- Mã QR của đối tượng (nếu có), ví dụ: `""`.

- **`totalCount`** (`int`):
	- Tổng số lượng đối tượng liên quan (nếu có), ví dụ: `0`.

- **`district`** (`string`):
	- Quận/huyện của đối tượng.
	- Ví dụ: `"Thạnh Phú"`.

- **`wardDistrict`** (`string`):
	- Phường/xã của đối tượng.
	- Ví dụ: `"An Nhơn"`.

- **`codeProject`** (`string`):
	- Mã dự án liên quan đến đối tượng.
	- Ví dụ: `"DA51423"`.

- **`projectAreaCode`** (`string`):
	- Mã khu vực dự án (nếu có), ví dụ: `""`.

---

#### Ví dụ
#### Request
```http
GET /api/HTKT/ManagementData/get-object-view?id=fb8c815a-27bb-2c22-7209-3a0bee3e8301
```

#### Response
```json
	{
	  "id": "fb8c815a-27bb-2c22-7209-3a0bee3e8301",
	  "nameObject": "Khu công nghiệp An Nhơn",
	  "geometry": {
		"type": "Polygon",
		"coordinates": [
		  [
			[106.5642958956085, 9.867865674642317],
			[106.58232712987973, 9.850919035287433],
			...
			[106.5642958956085, 9.867865674642317]
		  ]
		]
	  },
	  "listProperties": [
		{
		  "nameProperties": "Tên dự án",
		  "codeProperties": "Name",
		  "typeProperties": "string",
		  "isShow": true,
		  "isView": false,
		  "defalutValue": "Khu công nghiệp An Nhơn",
		  "orderProperties": 18,
		  "typeSystem": 2
		},
		{
		  "nameProperties": "Diện tích (ha)",
		  "codeProperties": "Acreage",
		  "typeProperties": "float",
		  "isShow": true,
		  "isView": false,
		  "defalutValue": "269.2",
		  "orderProperties": 27,
		  "typeSystem": 2
		}
	  ],
	  "idDirectory": "3572d80f-de05-5821-bb7a-3a07f1e4e673",
	  "properties": {
		"image2D": null,
		"stroke": "#864e0e",
		"strokeWidth": 2,
		"strokeOpacity": 1,
		"styleStroke": null,
		"fill": "#864e0e",
		"fillOpacity": 0.3
	  },
	  "object3D": null,
	  "tags": {
		"typeData": "newMultipolygon"
	  },
	  "isCheckImplementProperties": true,
	  "qrCodeObject": "",
	  "totalCount": 0,
	  "district": "Thạnh Phú",
	  "wardDistrict": "An Nhơn",
	  "codeProject": "DA51423",
	  "projectAreaCode": ""
	}
```
  
  
# API get-main-object-by-project-area

## Mô tả
Danh sách dự án của KCN,CCN cụm công nghiệp

### Đầu vào
- **`areaCode`** (string): Mã khu vực dự án cần lấy danh sách đối tượng.

### Đầu ra
- Trả về một đối tượng JSON chứa:
  - **mainObjects**: Danh sách đối tượng.
  - **propertiesSettingDtos**: setting của KCN,CCN.

### Chi tiết các thuộc tính của đối tượng trả về:

1. **`idDirectory`** (`string`):
   - ID của thư mục chứa đối tượng.
   - Ví dụ: `"ed40ebc3-8f00-8222-ed9f-3a07f1e9c08c"`.

2. **`nameObject`** (`string`):
   - Tên của đối tượng.
   - Ví dụ: `"CN02"`.

3. **`geometry`** (`object`):
   - Dữ liệu hình học (GeoJSON) của đối tượng.
   - Bao gồm:
     - **`type`** (`string`): Loại hình học, ví dụ `"MultiPolygon"`.
     - **`coordinates`** (`array`): Tọa độ của hình học.

4. **`properties`** (`object`):
   - Thuộc tính hiển thị của đối tượng.
   - Bao gồm:
     - **`image2D`** (`string`): URL của hình ảnh 2D (nếu có), ví dụ: `null`.
     - **`stroke`** (`string`): Màu đường viền, ví dụ: `"#a16dd5"`.
     - **`strokeWidth`** (`int`): Độ dày đường viền, ví dụ: `2`.
     - **`strokeOpacity`** (`float`): Độ trong suốt của đường viền, ví dụ: `1`.
     - **`styleStroke`** (`string`): Kiểu đường viền, ví dụ: `null`.
     - **`fill`** (`string`): Màu nền, ví dụ: `"#a16dd5"`.
     - **`fillOpacity`** (`float`): Độ trong suốt của màu nền, ví dụ: `0.3`.

5. **`object3D`** (`object`):
   - Dữ liệu 3D của đối tượng (nếu có), ví dụ: `null`.

6. **`district`** (`string`):
   - Mã quận/huyện của đối tượng.
   - Ví dụ: `"001053002"`.

7. **`wardDistrict`** (`string`):
   - Mã phường/xã của đối tượng.
   - Ví dụ: `"001053002005,001053002010"`.

8. **`codeProject`** (`string`):
   - Mã dự án liên quan đến đối tượng.
   - Ví dụ: `"DA52553"`.

9. **`projectAreaCode`** (`string`):
   - Mã khu vực dự án.
   - Ví dụ: `"963582b2-4bd9-dd24-30aa-3a0be8c4f74e"`.

10. **`tags`** (`object`):
    - Các thẻ liên quan đến đối tượng.
    - Ví dụ:
      ```json
      {
        "typeData": "newMultipolygon"
      }
      ```

11. **`lastModificationTime`** (`string`):
    - Thời gian chỉnh sửa lần cuối của đối tượng.
    - Ví dụ: `"2023-06-20T07:43:51.354Z"`.

12. **`lastModifierId`** (`string`):
    - ID của người chỉnh sửa lần cuối.
    - Ví dụ: `"16d7eb2b-aa64-5d66-de79-39fe2d19a269"`.

13. **`creationTime`** (`string`):
    - Thời gian tạo đối tượng.
    - Ví dụ: `"2023-06-20T07:41:10.851Z"`.

14. **`creatorId`** (`string`):
    - ID của người tạo đối tượng.
    - Ví dụ: `"16d7eb2b-aa64-5d66-de79-39fe2d19a269"`.

15. **`id`** (`string`):
    - ID duy nhất của đối tượng.
    - Ví dụ: `"9d13f104-a9c5-ac19-d11f-3a0be9ecf143"`.
	


---

#### Ví dụ
### Request
```http
GET /api/HTKT/ManagementData/get-main-object-by-project-area?areaCode=963582b2-4bd9-dd24-30aa-3a0be8c4f74e
```

#### Response

```json
{
    "mainObjects": [
        {
		  "idDirectory": "ed40ebc3-8f00-8222-ed9f-3a07f1e9c08c",
		  "nameObject": "CN02",
		  "geometry": {
			"type": "MultiPolygon",
			"coordinates": [
			  [
				[
				  [
					106.41333207632557,
					10.296305833372378
				  ],
				  [
					106.41389968294807,
					10.29609349236435
				  ],
				  [
					106.41365264149978,
					10.29543312380093
				  ],
				  [
					106.41340560005155,
					10.29477275523731
				  ],
				  [
					106.4125535144647,
					10.29509151950944
				  ],
				  [
					106.41304759736188,
					10.296412256637131
				  ],
				  [
					106.41324723077452,
					10.296337573998938
				  ],
				  [
					106.41333207632557,
					10.296305833372378
				  ]
				]
			  ]
			]
		  },
		  "properties": {
			"image2D": null,
			"stroke": "#a16dd5",
			"strokeWidth": 2,
			"strokeOpacity": 1,
			"styleStroke": null,
			"fill": "#a16dd5",
			"fillOpacity": 0.3
		  },
		  "object3D": null,
		  "district": "001053002",
		  "wardDistrict": "001053002005,001053002010",
		  "codeProject": "DA52553",
		  "projectAreaCode": "963582b2-4bd9-dd24-30aa-3a0be8c4f74e",
		  "tags": {
			"typeData": "newMultipolygon"
		  },
		  "lastModificationTime": "2023-06-20T07:43:51.354Z",
		  "lastModifierId": "16d7eb2b-aa64-5d66-de79-39fe2d19a269",
		  "creationTime": "2023-06-20T07:41:10.851Z",
		  "creatorId": "16d7eb2b-aa64-5d66-de79-39fe2d19a269",
		  "id": "9d13f104-a9c5-ac19-d11f-3a0be9ecf143"
    ],
    "propertiesSettingDtos": [
        {
		  "idDirectory": "8a9703ee-552f-750c-b005-3a0b7ca1a434",
		  "minZoom": 0,
		  "maxZoom": 0,
		  "image2D": null,
		  "object3D": "",
		  "texture3D": null,
		  "stroke": "#12a537",
		  "strokeWidth": 5,
		  "strokeOpacity": 1,
		  "styleStroke": "straightline",
		  "fill": "#12a537",
		  "fillOpacity": 0.3,
		  "tags": {
			"icon": "undefined"
		  },
		  "lastModificationTime": null,
		  "lastModifierId": null,
		  "creationTime": "2023-05-30T02:22:35.898Z",
		  "creatorId": "16d7eb2b-aa64-5d66-de79-39fe2d19a269",
		  "id": "9b303200-7d77-ccca-148e-3a0b7ca3b979"
		}
    ]
}
```

# API: `get-async`

## Mô tả
Get thông tin chi tiết của KCN, CCN cụm công nghiệp

---

## Đầu vào
- **`id`** (`Guid`): 
  - ID là KCN,CCN cụm công nghiệp.
  - Ví dụ: `"963582b2-4bd9-dd24-30aa-3a0be8c4f74e"`.

---

## Đầu ra
- **`Object`**:
  - Một đối tượng chứa thông tin chi tiết về khu vực dự án.
  - Cấu trúc:

### Chi tiết các thuộc tính của đối tượng trả về:

1. **`name`** (`string`):
   - Tên của khu vực dự án.
   - Ví dụ: `"Cụm công nghiệp Long Phước"`.

2. **`codeName`** (`string`):
   - Mã định danh của khu vực dự án.
   - Ví dụ: `"cumcongnghieplongphuoc"`.

3. **`geometry`** (`object`):
   - Dữ liệu hình học (GeoJSON) của khu vực dự án.
   - Bao gồm:
     - **`type`** (`string`): Loại hình học, ví dụ `"LineString"`.
     - **`coordinates`** (`array`): Tọa độ của hình học.

4. **`location`** (`string`):
   - Vị trí của khu vực dự án (nếu có), ví dụ: `null`.

5. **`urlIcon`** (`string`):
   - URL của biểu tượng đại diện cho khu vực dự án.
   - Ví dụ: `"https://map-xtdt.bentre.gov.vn/dataapp/image/a857bb7f-ce04-4a28-890f-eed991834ccf.png"`.

6. **`linkUrlInfo`** (`string`):
   - URL liên kết đến thông tin chi tiết của khu vực dự án (nếu có), ví dụ: `""`.

7. **`order`** (`int`):
   - Thứ tự hiển thị của khu vực dự án, ví dụ: `0`.

8. **`shortDescription`** (`string`):
   - Mô tả ngắn gọn về khu vực dự án (nếu có), ví dụ: `""`.

9. **`description`** (`string`):
   - Mô tả chi tiết về khu vực dự án (nếu có), ví dụ: `""`.

10. **`document`** (`string`):
    - Tài liệu liên quan đến khu vực dự án (nếu có), ví dụ: `null`.

11. **`parentId`** (`string`):
    - ID của khu vực cha (nếu có), ví dụ: `""`.

12. **`typeCategory`** (`string`):
    - Loại danh mục của khu vực dự án (nếu có), ví dụ: `""`.

13. **`showLabel`** (`string`):
    - Trạng thái hiển thị nhãn của khu vực dự án (nếu có), ví dụ: `""`.

14. **`isDeleted`** (`bool`):
    - Trạng thái xóa của khu vực dự án.
    - `true` nếu đã bị xóa, `false` nếu chưa bị xóa.

15. **`deleterId`** (`Guid`):
    - ID của người đã xóa khu vực dự án (nếu có), ví dụ: `null`.

16. **`deletionTime`** (`DateTime`):
    - Thời gian xóa khu vực dự án (nếu có), ví dụ: `null`.

17. **`lastModificationTime`** (`DateTime`):
    - Thời gian chỉnh sửa lần cuối của khu vực dự án.
    - Ví dụ: `"2024-08-30T01:16:38.908Z"`.

18. **`lastModifierId`** (`Guid`):
    - ID của người chỉnh sửa lần cuối.
    - Ví dụ: `"16d7eb2b-aa64-5d66-de79-39fe2d19a269"`.

19. **`creationTime`** (`DateTime`):
    - Thời gian tạo khu vực dự án.
    - Ví dụ: `"2023-06-20T02:17:53.743Z"`.

20. **`creatorId`** (`Guid`):
    - ID của người tạo khu vực dự án.
    - Ví dụ: `"16d7eb2b-aa64-5d66-de79-39fe2d19a269"`.

21. **`id`** (`Guid`):
    - ID duy nhất của khu vực dự án.
    - Ví dụ: `"963582b2-4bd9-dd24-30aa-3a0be8c4f74e"`.

---

#### Ví dụ
#### Request
```http
GET /api/HTKT/ProjectArea/get-async?id=963582b2-4bd9-dd24-30aa-3a0be8c4f74e
```

#### Response

```json
	{
	  "name": "Cụm công nghiệp Long Phước",
	  "codeName": "cumcongnghieplongphuoc",
	  "geometry": {
		"type": "LineString",
		"coordinates": [
		  [
			106.41137579364327,
			10.297309586270229
		  ],
		  [
			106.4148587975793,
			10.295889200866144
		  ],
		  ...
		  [
			106.41137579364327,
			10.297309586270229
		  ]
		]
	  },
	  "location": null,
	  "urlIcon": "https://map-xtdt.bentre.gov.vn/dataapp/image/a857bb7f-ce04-4a28-890f-eed991834ccf.png",
	  "linkUrlInfo": "",
	  "order": 0,
	  "shortDescription": "",
	  "description": "",
	  "document": null,
	  "parentId": "",
	  "typeCategory": "",
	  "showLabel": "",
	  "isDeleted": false,
	  "deleterId": null,
	  "deletionTime": null,
	  "lastModificationTime": "2024-08-30T01:16:38.908Z",
	  "lastModifierId": "16d7eb2b-aa64-5d66-de79-39fe2d19a269",
	  "creationTime": "2023-06-20T02:17:53.743Z",
	  "creatorId": "16d7eb2b-aa64-5d66-de79-39fe2d19a269",
	  "id": "963582b2-4bd9-dd24-30aa-3a0be8c4f74e"
	}
```


# API: get-list-for-client

## Mô tả
Danh sách lĩnh vực 

---

## Đầu vào
- API không yêu cầu tham số đầu vào.

---

## Đầu ra
- **`List<Object>`**:
  - Danh sách các đối tượng thuộc tính dành cho trang khách hàng.
  - Cấu trúc:

### Chi tiết các thuộc tính của đối tượng trả về:

1. **`nameTypeDirectory`** (`string`):
   - Tên lĩnh vực.
   - Ví dụ: `"Công nghiệp"`.

2. **`codeTypeDirectory`** (`string`):
   - Mã lĩnh vực.
   - Ví dụ: `"CONGNGHIEP"`.

3. **`idDirectory`** (`string`):
   - ID lĩnh vực.
   - Ví dụ: `"a63aeae4-28d7-41fd-9598-3a07f66ca4fa"`.

4. **`id`** (`string`):
   - ID của đối tượng.
   - Ví dụ: `"000f2197-694f-5791-9ef6-3a07f66ca556"`.

5. **`tag`** (`object`):
   - Các thẻ liên quan đến đối tượng.
   - Bao gồm:
     - **`public`** (`bool`): Trạng thái công khai của đối tượng, ví dụ: `true`.
     - **`icon`** (`string`): URL của biểu tượng đại diện, ví dụ: `"https://map-xtdt.bentre.gov.vn/dataapp/image/e4ecfd3f-759b-45be-8a62-f2c4a8fab2d4.png"`.
     - **`ParaSelected`** (`string`): Tham số được chọn (nếu có), ví dụ: `""`.

6. **`count`** (`int`):
   - Số lượng đối tượng trong thư mục.
   - Ví dụ: `70`.

---


#### Ví dụ
### Request
```http
GET /api/HTKT/PropertiesDirectory/get-list-for-client
```

#### Response
```json
	[
	  {
		"nameTypeDirectory": "Công nghiệp",
		"codeTypeDirectory": "CONGNGHIEP",
		"idDirectory": "a63aeae4-28d7-41fd-9598-3a07f66ca4fa",
		"id": "000f2197-694f-5791-9ef6-3a07f66ca556",
		"tag": {
		  "public": true,
		  "icon": "https://map-xtdt.bentre.gov.vn/dataapp/image/e4ecfd3f-759b-45be-8a62-f2c4a8fab2d4.png",
		  "ParaSelected": ""
		},
		"count": 70
	  },
	  {
		"nameTypeDirectory": "Du lịch",
		"codeTypeDirectory": "DULICH",
		"idDirectory": "51ea0a51-9dc7-f94f-e851-3a07fb5e7bf9",
		"id": "123e4567-e89b-12d3-a456-426614174000",
		"tag": {
		  "public": true,
		  "icon": "https://map-xtdt.bentre.gov.vn/dataapp/image/cb45c199-01e2-4583-b395-a252596d2588.png",
		  "ParaSelected": ""
		},
		"count": 39
	  }
	]

```

# API: search-main-object-by-geometry

## Mô tả
Sử dụng để tìm kiếm các đối tượng chính dựa trên hình học (Geometry) và danh sách ID thư mục.

---

## Đầu vào
- **`listID`** (`List<string>`): 
  - Danh sách ID của các thư mục cần tìm kiếm.
  - Ví dụ: `["ed40ebc3-8f00-8222-ed9f-3a07f1e9c08c", "a63aeae4-28d7-41fd-9598-3a07f66ca4fa"]`.

- **`geometry`** (`object`): 
  - Dữ liệu hình học (GeoJSON) để tìm kiếm.
  - Bao gồm:
    - **`type`** (`string`): Loại hình học, ví dụ `"Polygon"`.
    - **`coordinates`** (`array`): Tọa độ của hình học.

---

### Đầu ra
- Trả về một đối tượng JSON chứa:
  - **mainObjects**: Danh sách đối tượng.
  - **propertiesSettingDtos**: setting của KCN,CCN.

### Chi tiết các thuộc tính của đối tượng trả về:

1. **`idDirectory`** (`string`):
   - ID của thư mục chứa đối tượng.
   - Ví dụ: `"ed40ebc3-8f00-8222-ed9f-3a07f1e9c08c"`.

2. **`nameObject`** (`string`):
   - Tên của đối tượng.
   - Ví dụ: `"CN02"`.

3. **`geometry`** (`object`):
   - Dữ liệu hình học (GeoJSON) của đối tượng.
   - Bao gồm:
     - **`type`** (`string`): Loại hình học, ví dụ `"MultiPolygon"`.
     - **`coordinates`** (`array`): Tọa độ của hình học.

4. **`properties`** (`object`):
   - Thuộc tính hiển thị của đối tượng.
   - Bao gồm:
     - **`image2D`** (`string`): URL của hình ảnh 2D (nếu có), ví dụ: `null`.
     - **`stroke`** (`string`): Màu đường viền, ví dụ: `"#a16dd5"`.
     - **`strokeWidth`** (`int`): Độ dày đường viền, ví dụ: `2`.
     - **`strokeOpacity`** (`float`): Độ trong suốt của đường viền, ví dụ: `1`.
     - **`styleStroke`** (`string`): Kiểu đường viền, ví dụ: `null`.
     - **`fill`** (`string`): Màu nền, ví dụ: `"#a16dd5"`.
     - **`fillOpacity`** (`float`): Độ trong suốt của màu nền, ví dụ: `0.3`.

5. **`object3D`** (`object`):
   - Dữ liệu 3D của đối tượng (nếu có), ví dụ: `null`.

6. **`district`** (`string`):
   - Mã quận/huyện của đối tượng.
   - Ví dụ: `"001053002"`.

7. **`wardDistrict`** (`string`):
   - Mã phường/xã của đối tượng.
   - Ví dụ: `"001053002005,001053002010"`.

8. **`codeProject`** (`string`):
   - Mã dự án liên quan đến đối tượng.
   - Ví dụ: `"DA52553"`.

9. **`projectAreaCode`** (`string`):
   - Mã khu vực dự án.
   - Ví dụ: `"963582b2-4bd9-dd24-30aa-3a0be8c4f74e"`.

10. **`tags`** (`object`):
    - Các thẻ liên quan đến đối tượng.
    - Ví dụ:
      ```json
      {
        "typeData": "newMultipolygon"
      }
      ```

11. **`lastModificationTime`** (`string`):
    - Thời gian chỉnh sửa lần cuối của đối tượng.
    - Ví dụ: `"2023-06-20T07:43:51.354Z"`.

12. **`lastModifierId`** (`string`):
    - ID của người chỉnh sửa lần cuối.
    - Ví dụ: `"16d7eb2b-aa64-5d66-de79-39fe2d19a269"`.

13. **`creationTime`** (`string`):
    - Thời gian tạo đối tượng.
    - Ví dụ: `"2023-06-20T07:41:10.851Z"`.

14. **`creatorId`** (`string`):
    - ID của người tạo đối tượng.
    - Ví dụ: `"16d7eb2b-aa64-5d66-de79-39fe2d19a269"`.

15. **`id`** (`string`):
    - ID duy nhất của đối tượng.
    - Ví dụ: `"9d13f104-a9c5-ac19-d11f-3a0be9ecf143"`.


## Ví dụ đầu vào
#### Request
```http
POST /api/HTKT/ManagementData/search-main-object-by-geometry
```
```json
{
  "listID": ["ed40ebc3-8f00-8222-ed9f-3a07f1e9c08c", "a63aeae4-28d7-41fd-9598-3a07f66ca4fa"],
  "geometry": {
    "type": "Polygon",
    "coordinates": [
      [
        [106.41333207632557, 10.296305833372378],
        [106.41389968294807, 10.29609349236435],
        [106.41365264149978, 10.29543312380093],
        [106.41333207632557, 10.296305833372378]
      ]
    ]
  }
}
```

#### Response
```json
{
    "mainObjects": [
        {
		  "idDirectory": "ed40ebc3-8f00-8222-ed9f-3a07f1e9c08c",
		  "nameObject": "CN02",
		  "geometry": {
			"type": "MultiPolygon",
			"coordinates": [
			  [
				[
				  [
					106.41333207632557,
					10.296305833372378
				  ],
				  [
					106.41389968294807,
					10.29609349236435
				  ],
				  [
					106.41365264149978,
					10.29543312380093
				  ],
				  [
					106.41340560005155,
					10.29477275523731
				  ],
				  [
					106.4125535144647,
					10.29509151950944
				  ],
				  [
					106.41304759736188,
					10.296412256637131
				  ],
				  [
					106.41324723077452,
					10.296337573998938
				  ],
				  [
					106.41333207632557,
					10.296305833372378
				  ]
				]
			  ]
			]
		  },
		  "properties": {
			"image2D": null,
			"stroke": "#a16dd5",
			"strokeWidth": 2,
			"strokeOpacity": 1,
			"styleStroke": null,
			"fill": "#a16dd5",
			"fillOpacity": 0.3
		  },
		  "object3D": null,
		  "district": "001053002",
		  "wardDistrict": "001053002005,001053002010",
		  "codeProject": "DA52553",
		  "projectAreaCode": "963582b2-4bd9-dd24-30aa-3a0be8c4f74e",
		  "tags": {
			"typeData": "newMultipolygon"
		  },
		  "lastModificationTime": "2023-06-20T07:43:51.354Z",
		  "lastModifierId": "16d7eb2b-aa64-5d66-de79-39fe2d19a269",
		  "creationTime": "2023-06-20T07:41:10.851Z",
		  "creatorId": "16d7eb2b-aa64-5d66-de79-39fe2d19a269",
		  "id": "9d13f104-a9c5-ac19-d11f-3a0be9ecf143"
    ],
    "propertiesSettingDtos": [
        {
		  "idDirectory": "8a9703ee-552f-750c-b005-3a0b7ca1a434",
		  "minZoom": 0,
		  "maxZoom": 0,
		  "image2D": null,
		  "object3D": "",
		  "texture3D": null,
		  "stroke": "#12a537",
		  "strokeWidth": 5,
		  "strokeOpacity": 1,
		  "styleStroke": "straightline",
		  "fill": "#12a537",
		  "fillOpacity": 0.3,
		  "tags": {
			"icon": "undefined"
		  },
		  "lastModificationTime": null,
		  "lastModifierId": null,
		  "creationTime": "2023-05-30T02:22:35.898Z",
		  "creatorId": "16d7eb2b-aa64-5d66-de79-39fe2d19a269",
		  "id": "9b303200-7d77-ccca-148e-3a0b7ca3b979"
		}
    ]
}
```




