# Rush Subspace
Reproduce steps: 

1. Go to `subspaces/subspace4/subspace4_lib`, Run `rush add -p moment` (You can choose any NPM dependencies)
2. Check `pnpm-lock.yaml` changes. You will find the `pnpm-lock.yaml` under subspace4 get updated. But `pnpm-lock.yaml` under subspace1 is not updated. 
3. Ok, now, let's run `rush update --to subspace1_lib` . You will find `pnpm-lock.yaml` under subspace1 still not updated, **this is not correct!** 
4. Let's run `rush update --to subspace1_lib --recheck`, finally, the `pnpm-lock.yaml` under subspace1 gets updated. 

So the problem we are trying to solve is  let `rush update` be able to detect changes in another subspace for injected installation case, and update the `pnpm-lock.yaml` accordingly.