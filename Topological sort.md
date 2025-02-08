






``` java

class Solution {
    // Function to return list containing vertices in Topological order.
    static ArrayList<Integer> topologicalSort(ArrayList<ArrayList<Integer>> adj) {
        Stack<Integer> st=new Stack<>();
        
        int V=adj.size();
        
        boolean visited[]=new boolean[V];
        
        for(int i=0;i<V;i++)
        {
            if(!visited[i])
            {
                dfs(i,visited,adj,st);
            }
        }
        
        
        ArrayList<Integer> ans=new ArrayList<>();
        
        
        while(!st.isEmpty())
        {
            ans.add(st.pop());
        }
        
        return ans;
    }
    public static void dfs(int node,boolean visited[],ArrayList<ArrayList<Integer>> adj,Stack<Integer> st)
    {
        visited[node]=true;
        
        
        for(int x:adj.get(node))
        {
            if(!visited[x])
            {
                dfs(x,visited,adj,st);
            }
        }
        st.push(node);
    }
}
