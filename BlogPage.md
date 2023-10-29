# 单例模式:from effective c++

```c++
class Singleton {
  private:
    Singleton(){}
    ~Singleton(){}
    Singleton(const Singleton& singleton) = delete;
    Singleton& operator=(const Singleton& singleton) = delete;
  public:
    static Singleton& GetInstance() {
        static Singleton instance;
        return instance;
    }
};
```

# ECS:how to manage the scene

```c++
class Scene {
    std::vector<Entity*> entities;
    virtual void OnUpdate();
}
class Entity {
    mat4 Transform;
    string name;
    virtual void OnUpdate() override;
};

class Light : public Entity{
    vec3 Color;
    float Intensity;
    Type type;
};

class AudioMesh : public Entity {
    AudioClip* clip;
    Mesh* mesh;
};

class Player : public AudioMesh {

};
/// 使用继承的方式管理场景需要建立一个一个不同的类，在update函数中去写逻辑
// 组合大于继承
class Entity {
    mat4 Transform;
    string name;
    std::vector<Component*> components;
}

struct Component {
    
};

struct AudioComponent :public Component {
    AudioClip* clip;
}; 
struct MeshComponent :public Component{
    Mesh* mesh;
}; 

struct LightComponent : public Component{
    vec3 Color;
    float Intensity;
    Type type;
};

Scene::OnUpdate {
    for(auto* entity : Entities) {
        if(has mesh component) {
            submit
        }
    }
}
entity作用是使不同component之间相互交流，entity is a ID， entt去枚举
```

