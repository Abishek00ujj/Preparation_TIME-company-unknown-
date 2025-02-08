




``` java
class Solution {
    // Function to detect cycle in a directed graph.
    public boolean isCyclic(int V, ArrayList<ArrayList<Integer>> adj) {
        boolean visited[]=new boolean[V+1];
        
        boolean path[]=new boolean[V+1];
        
        for(int i=0;i<V;i++)
        {
            if(!visited[i] && dfs(i,V,adj,visited,path))
            {
                return true;
            }
        }
        return false;
    }
    
    public boolean dfs(int node,int V,ArrayList<ArrayList<Integer>> adj,boolean path[],boolean visited[])
    {
        visited[node]=true;
        path[node]=true;
        
        for(int x:adj.get(node))
        {
            if(path[x])
            {
                return true;
            }
            if(!visited[x])
            {
                if(dfs(x,V,adj,path,visited))
                {
                    return true;
                }
            }
        }
        path[node]=false;
        return false;
    }
}
