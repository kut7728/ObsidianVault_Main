## Text Mesh Pro

화면에 텍스트를 띄우는 인스턴스

  

캔버스 인스펙터의 렌더링 모드에 따라

- 스크린 공간 - 오버레이 : 게임 화면에 띄워지는 텍스트
- 스크린 공간 - 카메라 : 카메라에 띄워지는 텍스트
- 월드 공간 : 다른 객체들처럼 표현되는 텍스트

  

## 클릭시 TMP로 객체 이름 출력 후 파괴 스크립트

```C#
void Update()
    {
        if(Input.GetMouseButtonDown(0)){
            Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);
            RaycastHit hit;

            if (Physics.Raycast(ray, out hit)) {
                // Debug.Log(hit.transform.gameObject.name);
                tmpText.text = hit.transform.gameObject.name;
                Destroy(hit.transform.gameObject);

            }
        }
    }
```

  

## 오브젝트 생성 스크립트

```C#
public GameObject go;
    public Transform point;
    public Transform parent;
    int num;


    void Start()
    {
        // GameObject spawnobj = Instantiate(go, point.position, point.rotation, parent);
        // spawnobj.name = "new";

        num = 0;
    }

    void Update()
    {
        if (Input.GetKeyDown("space")) {
            GameObject spawnobj = Instantiate(go, point.position, point.rotation, parent);
            spawnobj.name = "new"+num;
            num++;

            float t = Random.Range(0.5f, 2.0f);
            Destroy(spawnobj, t);
        }
    }
```