
## Solution 1 (CPP). Hash Table + Trie
```cpp

class FileSystem {
public:
    
    struct TrieNode {        
        unordered_map<string,TrieNode*> child;
        bool isFile;
        string content;
        TrieNode() : isFile(false), content("") { }
    };
    
    TrieNode* root;
    
    TrieNode* toPath(string& path) {
        TrieNode* p=root;
        stringstream ss(path);
        string s;
        while (getline(ss, s, '/')) {
            if(s.size()) {
                if (p->child[s]==nullptr)
                    p->child[s] = new TrieNode();
                p=p->child[s];
            }
        }
        return p;
    }
    
    FileSystem() : root(new TrieNode()) {  }
    
    vector<string> ls(string path) {
        TrieNode* p=toPath(path);
        if(p->isFile) {
            string s = path.substr(path.find_last_of('/')+1);
            return {s};
        };
        
        vector<string> res;
        for(auto& a : p->child) res.push_back(a.first);
        sort(res.begin(), res.end());
        return res;
    }
    
    void mkdir(string path) {
        toPath(path);
    }
    
    void addContentToFile(string path, string content) {
        TrieNode* p=toPath(path);
        p->content+=content;
        p->isFile=true;
    }
    
    string readContentFromFile(string path) {
        TrieNode* p=toPath(path);
        return p->content;
    }
       
};
```
