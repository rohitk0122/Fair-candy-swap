# Fair-candy-swap
int sumA = 0, sumB = 0;
        
        // Calculate the sum of Alice's and Bob's candy counts
        for (int a : aliceSizes) sumA += a;
        for (int b : bobSizes) sumB += b;
        
        // Calculate the difference divided by 2
        int delta = (sumA - sumB) / 2;
        
        // Put all Bob's candy counts into a set for quick lookup
        Set<Integer> setB = new HashSet<>();
        for (int b : bobSizes) setB.add(b);
        
        // Try to find a valid pair (x, y)
        for (int x : aliceSizes) {
            int y = x - delta;
            if (setB.contains(y)) {
                return new int[]{x, y};
            }
        }
        
        // This line will never be reached because the problem guarantees that at least one solution exists
        throw new IllegalStateException("No valid solution found");
