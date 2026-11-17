# Knowledge related to Jest unit tests

### jest.requireActual('react') vs jest.requireMock('react')
- jest.requireMock: Gets the mocked version of a module
- jest.requireActual: Gets the real implementation of a module, bypassing Jest mocks. Useful when mocking a lightweight react element.

### clearAllMocks vs resetAllMocks
- clearAllMocks: Clears mock call history but keeps mock implementations
```
const mockFn = jest.fn().mockReturnValue('hello');
		mockFn();
		expect(mockFn).toHaveBeenCalledTimes(1);
		jest.clearAllMocks();
		expect(mockFn).toHaveBeenCalledTimes(0);
		expect(mockFn()).toBe('hello'); // Implementation 유지
```
- resetAllMocks: Clears mock call history and resets mock implementations
```
const mockFn = jest.fn().mockReturnValue('hello');
		mockFn();
		expect(mockFn).toHaveBeenCalledTimes(1);
		jest.resetAllMocks();
		expect(mockFn).toHaveBeenCalledTimes(0);
		expect(mockFn()).toBe(undefined); // Implementation 초기화
```

### ; in front of mockReturnValue()
- ;(hooks.useApplicationData as jest.Mock).mockReturnValue()
;(hooks.useUser as jest.Mock).mockReturnValue()
A reason that you put ; is to prevent Javascript’s automatic semicolon insertion from treating the next line’s ( as a continuation of the previous line.)